import java.util.Arrays;
import java.util.Scanner;

/**
 * A chess game. Contains a main method to play chess.
 * @author Pascale Launay
 */
public class Chess {

    /**
     * Chess playing program.
     * @param args NONE
     */
    public static void main(String[] args) {
        // play chess
        Chess chess = new Chess();
        chess.playChess();
    }

    /**
     * Play a chess game
     */
    public void playChess() {
        Scanner scanner = new Scanner(System.in);
        
        // ask for the piece properties
        System.out.print("Give the piece name " + Arrays.asList(PieceName.values()) + ": ");
        PieceName name = PieceName.valueOf(Keyboard.readLine());
        System.out.print("Give the piece color " + Arrays.asList(PieceColor.values()) + ": ");
        PieceColor color = PieceColor.valueOf(Keyboard.readLine());

         // Demande de la position initiale
         System.out.println("Give the piece location");
         System.out.print("x: ");
         int x = scanner.nextInt();
         System.out.print("y: ");
         int y = scanner.nextInt();
        // make a piece
        Piece piece = new Piece(name, color, x, y);
// Boucle pour déplacer la pièce
while (true) {
    System.out.print("Move piece ? (y/n) ");
    String moveAgain = scanner.next();
    if (!moveAgain.equalsIgnoreCase("y")) {
        break;
    }

    System.out.println("Give the piece movement");
    System.out.print("dx: ");
    int dx = scanner.nextInt();
    System.out.print("dy: ");
    int dy = scanner.nextInt();

    if (piece.isValidMove(dx, dy)) {
        piece.move(dx, dy);
        System.out.println(piece);
    } else {
        System.out.println("Error. This is not a valid move");
        System.out.println(piece);
    }
}

scanner.close();


        // ask for the movement properties and move the piece
        while (true) {
            System.out.println("Give the piece movement (enter 0 0 to exit)");
            System.out.print(" dx: ");
            int dx = Keyboard.readInt();
            System.out.print(" dy: ");
            int dy = Keyboard.readInt();

            // Sortir si l'utilisateur entre 0 0
            if (dx == 0 && dy == 0) {
                break;
            }

            // Vérifier si le mouvement est valide
            if (piece.isValidMove(dx, dy)) {
                // Déplacer la pièce
                piece.move(dx, dy);
                System.out.println("The piece after moving: " + piece);
            } else {
                System.out.println("Invalid move. Try again.");
            }    
        }
    }
}
