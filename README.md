# ReToDoS

This project provides a simple CLI to manage a to-do list. The CLI is written in Rust and manages all data with Redis.

## Prerequisites

The CLI offered by this project assumes a local Redis server on the default port. You need Cargo to build and install the project.

## Installation

You can install the CLI with Cargo by running the following command. This will build the project and install the CLI binary in `$HOME/.cargo/bin/retodos`. Make sure to run the command in the root of the repository.

```bash
cargo install --path .
```

## Usage

See `retodos --help` for a list of available commands.

### Examples

The following example shows how to add new items to the to-do list and how to view them.

```bash
# Add new ToDo items (on April 10, 2022)
retodos add "Buy milk" "tomorrow 9:00"
retodos add "Do homework" "19:00"
retodos add "Call mom" "next fri 11:30"

retodos list # Prints...
# 1. Do homework (Due by 19:00, 10.04.2022)
# 2. Buy milk (Due by 09:00, 11.04.2022)
# 3. Call mom (Due by 11:30, 22.04.2022)
```

The next example demonstrates how to delete items from the to-do list (based on the list from above).

```bash
# Delete item with ordinal 2
retodos delete 2

retodos list # Prints...
# 1. Do homework (Due by 19:00, 10.04.2022)
# 3. Call mom (Due by 11:30, 22.04.2022)

# Delete all items
retodos delete --all

retodos list # Prints...
# No ToDos. All done!
```

It is also possible to modify a ToDo item, as shown in the following example, using the items added in the first example.

```bash
# Modify title of item with ordinal 1
retodos update 1 --title "Do work"

# Modify due date of item with ordinal 3
retodos update 3 --due-date "10:00"

retodos list # Prints...
# 1. Call mom (Due by 10:00, 10.04.2022)
# 2. Do work (Due by 19:00, 10.04.2022)
# 3. Buy milk (Due by 09:00, 11.04.2022)
```
