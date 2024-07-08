import java.util.Random;
import java.util.Scanner;

public class GuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        boolean playAgain = true;
        int totalScore = 0;

        while (playAgain) {
            int numberToGuess = random.nextInt(60) + 1;
            int attempts = 0;
            int maxAttempts = 5;
            boolean guessedCorrectly = false;

            System.out.println("Guess the number between 1 and 60. You have " + maxAttempts + " attempts.");

            while (attempts < maxAttempts) {
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();
                attempts++;

                if (userGuess == numberToGuess) {
                    System.out.println("Yay!! You guessed the correct number.");
                    totalScore += (maxAttempts - attempts + 1);
                    guessedCorrectly = true;
                    break;
                } else if (userGuess < numberToGuess) {
                    System.out.println("Too low!");
                } else {
                    System.out.println("Too high!");
                }
            }

            if (!guessedCorrectly) {
                System.out.println("Sorry, you've used all your attempts. The correct number was " + numberToGuess);
            }

            System.out.print("Do you want to play again? (1/0): ");
            scanner.nextLine();  // Consume newline left-over
            String response = scanner.nextLine();

            if (!response.equalsIgnoreCase("1")) {
                playAgain = false;
            }
        }

        System.out.println("Your total score is: " + totalScore);
        scanner.close();
    }
}
