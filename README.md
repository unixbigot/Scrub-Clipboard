# Scrub-Clipboard
MacOS automator workflow to add a "scrub cllipboard" option to the services menu

# The problem

Sometimes you want to make sure the clipboard is empty (I just pasted
sensitive information).

You can do this by select one character and copy, but it's two actions.

# The solution

Check out and install the workflow in this repo.   Run it

1. Create the workflow (or just use the existing copy)
 * Open Automator
 * Choose file->new and select "Service"
 * Search 'clip' in library and drag over 'Get Contents of Clipboard'
 * Search 'script' in library and drag over 'Run shell script'
 * Make the script `pbcopy </dev/null`
 * Save
 * Do file->export to "Scrub Clipboard.workflow"
1. Install the workflow
 * Click the saved workflow to install it
1. Set a keyboard shortcut
 * Open System preferences, go to keyboard tab, select shortcuts
 * Find Scrub Clipboard in the services section and set a shortcut
 * I chose cmd-option-x to mean "cut nothing"

# Why can't I do it with applescript instead of shell script

I don't know, the apple script below SHOULD work but does not.  Send a PR if you get it working.it

```
on run {input, parameters}
 
 
          tell application "System Events" to set the clipboard to ""
 
          return input
end run
```
