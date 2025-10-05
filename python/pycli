# my_cli.py
import argparse

def greet_command(args):
    """Handles the 'greet' subcommand."""
    print(f"Hello, {args.name}!")
    if args.shout:
        print("A very nice day to you!")
        
def calc_command(args):
    """Handles the 'calc' subcommand."""
    if args.operation == 'add':
        result = args.x + args.y
        print(f"The sum of {args.x} and {args.y} is {result}")
    elif args.operation == 'multiply':
        result = args.x * args.y
        print(f"The product of {args.x} and {args.y} is {result}")

def main():
    """Main function to parse arguments and call subcommands."""
    parser = argparse.ArgumentParser(
        description="A simple Python CLI tool with multiple subcommands.",
        epilog="Example: my_cli.py greet --name World or my_cli.py calc add 5 3"
    )
    
    subparsers = parser.add_subparsers(dest='command', help='Available commands')
    subparsers.required = True

    # Subparser for the 'greet' command
    greet_parser = subparsers.add_parser('greet', help='Greet a person')
    greet_parser.add_argument('--name', type=str, default='World', help='The name of the person to greet.')
    greet_parser.add_argument('--shout', action='store_true', help='Shout the greeting.')
    greet_parser.set_defaults(func=greet_command)

    # Subparser for the 'calc' command
    calc_parser = subparsers.add_parser('calc', help='Perform a calculation')
    calc_subparsers = calc_parser.add_subparsers(dest='operation', help='Calculation operations')
    calc_subparsers.required = True

    # Add operation
    add_parser = calc_subparsers.add_parser('add', help='Add two numbers')
    add_parser.add_argument('x', type=int, help='The first number.')
    add_parser.add_argument('y', type=int, help='The second number.')
    add_parser.set_defaults(func=calc_command)

    # Multiply operation
    multiply_parser = calc_subparsers.add_parser('multiply', help='Multiply two numbers')
    multiply_parser.add_argument('x', type=int, help='The first number.')
    multiply_parser.add_argument('y', type=int, help='The second number.')
    multiply_parser.set_defaults(func=calc_command)

    args = parser.parse_args()
    args.func(args)

if __name__ == '__main__':
    main()

