# codealpha.tasks
import random

def hangman():
    # Predefined list of words
    words = ["apple", "tiger", "plane", "chair", "house"]
    word = random.choice(words)  # Pick a random word
    guessed = ["_"] * len(word)  # Display blanks
    attempts = 6
    guessed_letters = set()

    print("Welcome to Hangman!")
    print("Guess the word:")
    print(" ".join(guessed))

    while attempts > 0 and "_" in guessed:
        guess = input("Enter a letter: ").lower()

        # Input validation
        if len(guess) != 1 or not guess.isalpha():
            print("Please enter a single letter.")
            continue
        if guess in guessed_letters:
            print("You already guessed that letter.")
            continue

        guessed_letters.add(guess)

        if guess in word:
            print("Good guess!")
            for i, letter in enumerate(word):
                if letter == guess:
                    guessed[i] = guess
        else:
            attempts -= 1
            print(f"Wrong guess! Attempts left: {attempts}")

        print(" ".join(guessed))

    if "_" not in guessed:
        print(f"Congratulations! You guessed the word: {word}")
    else:
        print(f"Game over! The word was: {word}")

# Run the game
if __name__ == "__main__":
    hangman()
