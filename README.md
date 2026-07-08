def caesar_cipher(text, shift, mode):
    result = ""

    # Reverse the shift for decryption
    if mode.lower() == "decrypt":
        shift = -shift

    for char in text:
        if char.isalpha():
            # Determine ASCII offset based on case
            offset = ord('A') if char.isupper() else ord('a')

            # Shift character and wrap around alphabet
            new_char = chr((ord(char) - offset + shift) % 26 + offset)
            result += new_char
        else:
            # Keep spaces, numbers, and symbols unchanged
            result += char

    return result


def main():
    print("=== Caesar Cipher Program ===")

    while True:
        choice = input("\nChoose an option (encrypt/decrypt/exit): ").lower()

        if choice == "exit":
            print("Goodbye!")
            break

        if choice not in ["encrypt", "decrypt"]:
            print("Invalid option. Please choose 'encrypt', 'decrypt', or 'exit'.")
            continue

        message = input("Enter your message: ")

        try:
            shift = int(input("Enter shift value: "))
        except ValueError:
            print("Shift value must be an integer.")
            continue

        result = caesar_cipher(message, shift, choice)

        print(f"\nResult: {result}")


if __name__ == "__main__":
    main()
