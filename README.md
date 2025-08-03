import os
import time
import sys

ascii_art = r'''
   ╔═══╗    ╔══╗    ╔===== +_)


       discord mod
'''

status_lines = [
    ("Found ROBLOX @ (PID: 14228)", 2.5),
    ("WARNING: QApplication was not created in the main() thread.", 0.5),
    ("Waiting for the game to be fully loaded...", 2.5),
    ("Game is fully loaded, injecting...", 2.5),
    ("Injected!", 2.5)
]

def overwrite_log(text, delay=1):
    try:
        columns = os.get_terminal_size().columns
    except:
        columns = 80  # fallback in environments like IDLE

    timestamp = time.strftime("[ %Y-%m-%d %H:%M:%S ]", time.localtime())
    full_line = f"\033[91m{timestamp}\033[0m {text}"
    sys.stdout.write('\r' + ' ' * columns)
    sys.stdout.flush()
    sys.stdout.write('\r' + full_line)
    sys.stdout.flush()
    time.sleep(delay)
    sys.stdout.write('\r' + ' ' * columns)
    sys.stdout.flush()

def main():
    os.system("title Steam - Loader" if os.name == "nt" else "")
    os.system("cls" if os.name == "nt" else "clear")
    
    print(ascii_art)
    print("\n [-] Key: ", end="")
    input()
    
    print("\n [-] Verifying key...")
    time.sleep(2)
    print(" [-] Key accepted!")
    time.sleep(1)
    print(" [-] Starting...\n")
    time.sleep(2)
    
    for line, delay in status_lines:
        overwrite_log(line, delay)
    
    print("\n [/] If Failed to load.")
    print(" [*] Please contact user for support.")
    input("\n Press Enter to exit You Are Injected...")

if __name__ == "__main__":
    main()
