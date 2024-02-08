import os

def read_file(file_path):
    try:
        with open(file_path, 'r', encoding='utf-8') as file:
            content = file.read()
        return content
    except FileNotFoundError:
        print(f"Error: File '{file_path}' not found.")
        return None
    except Exception as e:
        print(f"Error reading file: {e}")
        return None

def write_file(file_path, content):
    try:
        with open(file_path, 'w', encoding='utf-8') as file:
            file.write(content)
    except Exception as e:
        print(f"Error writing to file: {e}")

def analyze_text(text):
    word_count = len(text.split())
    line_count = text.count('\n') + 1
    char_count = len(text)
    return word_count, line_count, char_count

def modify_text(text, old_word, new_word):
    modified_text = text.replace(old_word, new_word)
    return modified_text

if __name__ == "__main__":
    file_path = "sample.txt"  # Replace with your actual file path
    original_content = read_file(file_path)

    if original_content is not None:
        # Perform analysis
        word_count, line_count, char_count = analyze_text(original_content)
        print(f"Word Count: {word_count}")
        print(f"Line Count: {line_count}")
        print(f"Character Count: {char_count}")

        # Modify content
        old_word = "example"
        new_word = "modified"
        modified_content = modify_text(original_content, old_word, new_word)

        # Write modified content back to file
        write_file(file_path, modified_content)

        print(f"\nFile '{file_path}' successfully modified.")
    else:
        print("Exiting due to errors.")

