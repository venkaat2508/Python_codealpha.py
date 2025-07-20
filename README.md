import random

# List of possible words
word_list = ["python", "code", "alpha", "hangman", "script"]

# Randomly choose one word from the list
secret_word = random.choice(word_list)
guessed_letters = ""  # Store the letters guessed by the user
remaining_attempts = 6  # Number of wrong attempts allowed

print("🎮 Welcome to the Hangman Game!")
print("Try to guess the word one letter at a time.")

# Main game loop
while remaining_attempts > 0:
    display_word = ""

    for letter in secret_word:
        if letter in guessed_letters:
            display_word += letter + " "
        else:
            display_word += "_ "

    print("\nWord:", display_word.strip())

    # Check if the user has guessed all letters
    if "_" not in display_word:
        print("🎉 Great job! You guessed the word:", secret_word)
        break

    guess = input("Guess a letter: ").lower()

    if guess in guessed_letters:
        print("⚠️ You already guessed that letter.")
        continue

    guessed_letters += guess

    if guess not in secret_word:
        remaining_attempts -= 1
        print(f"❌ Incorrect! You have {remaining_attempts} attempts left.")

if remaining_attempts == 0:
    print("💀 Game over! The word was:", secret_word)
