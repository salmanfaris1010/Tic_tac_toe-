# Tic_tac_toe-
It is a cool game to play in free time with your friend 



def print_board(board):
    for i, row in enumerate(board):
        row_str = " "
        for j, value in enumerate(row):
            row_str += value
            if j != len(row) - 1:
                row_str += " | "

        print(row_str)
        if i != len(row) - 1:
            print("__________")


def get_move(turn, board):
    while True:
        row = int(input("\n raw: "))
        col = int(input(" col: \n"))

        if row < 1 or row > len(board):
            print("invalid raw please try aganin ")
        elif col < 1 or col > len(board):
            print("invalid colum ,please try again")
        elif board[row - 1][col - 1] != " ":
            print("there is already picked")
        else:
            break

    board[row - 1][col - 1] = turn


board = [[" ", " ", " "], [" ", " ", " "], [" ", " ", " "]]


def check_win(board, turn):
    lines = [
        [(0, 0), (0, 1), (0, 2)],
        [(1, 0), (1, 1), (1, 2)],
        [(2, 0), (2, 1), (2, 2)],
        [(0, 0), (1, 0), (2, 0)],
        [(0, 1), (1, 1), (2, 1)],
        [(0, 2), (1, 2), (2, 2)],
        [(0, 0), (1, 1), (2, 2)],
        [(0, 2), (1, 1), (2, 0)],
    ]

    for line in lines:
        win = True
        for pos in line:
            row, col = pos
        if board[row][col] != turn:
            win = False
            break
        if win:
            return True
        return False


turn = "x"
turn_number = 0
print_board(board)


while turn_number < 9:
    print("it is the turn of ", turn, "player please enter your turn ")
    get_move(turn, board)
    print_board(board)
    winner = check_win(board, turn)
    if winner:
        print("the winner is ", turn, "player ")

        break

    if turn == "x":
        turn = "o"
    else:
        turn = "x"
    turn_number += 1


if turn_number == 9:
    print("the game is tie !!!")
    ask = input("wanna another game please game(y/n): ?")
    if ask == "y":

        print("restart the game ")
    else:
        print("good bye")
else:
    winner = True

