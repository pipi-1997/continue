# Continue CLI Terminal UI spec

This spec is **complete** as of 2026-02-22.

## Stack

The Continue CLI uses Ink as a react TUI library.

## Layout Structure

### Main Areas

1. **Header Bar** (top)
   - App title "Continue" on the left
   - Mode indicator ([normal], [plan], [auto]) on the right
   - Height: 1 row

2. **Chat Area** (middle, scrollable)
   - User messages (right-aligned)
   - Assistant messages (left-aligned)
   - Tool calls with status indicators
   - Scrollable history

3. **Input Area** (bottom)
   - Multi-line text input
   - Prompt indicator ($ for normal, > for shell mode)
   - Placeholder text when empty
   - Height: 3-10 rows (dynamic)

4. **Status Bar** (bottom-left corner)
   - Current working directory or git branch info
   - Shows git branch if in a git repo
   - Shows owner/repo if in a gh repo and enough columns
   - Shows cwd if not in git

## cwd/git display

The lower left corner of the TUI should display

- the current git branch if in a git repo
- also the current owner/repo if enough columns are available to display and it's a gh repo
- if not in git, the cwd

## Input Modes

### Normal Mode
- Prompt shows ">"
- Full chat input with @ file suggestions and / slash commands

### Shell Mode
- Activated when input starts with "!"
- Prompt shows "$"
- Input border turns yellow
- Executes commands directly in terminal

### Slash Command Mode
- Activated when input starts with "/"
- Shows available commands in dropdown

## Color Scheme

- Primary: Blue (#3B82F6)
- Success: Green (#22C55E)
- Warning: Yellow (#EAB308)
- Error: Red (#EF4444)
- Text: White/Gray
- Background: Dark (terminal default)

## Keyboard Shortcuts

- Enter: Submit message
- Shift+Enter: New line
- Ctrl+C: Exit (double-tap within 1 second)
- Shift+Tab: Cycle modes
- Esc: Cancel/dismiss

## Status Indicators

- Loading: Spinner animation
- Thinking: Dots animation
- Tool running: Yellow border
- Error: Red border with error message
