---
title: "Nautilus script to copy paths of selected files."
date: 2007-09-02
forum: Desktop Environments
---

### Post by sandipchitale on 2007-09-02
[NOTE: This is my first nautilus script]

A simple nautilus script to copy paths of selected files (one per line) into the system clipboard.

Just copy/paste the following script:
[FONT="Courier New"]
#!/usr/bin/python

import pygtk
pygtk.require('2.0')
import gtk
import os

# get the clipboard
clipboard = gtk.clipboard_get()

# set the clipboard text data
clipboard.set_text(os.environ['NAUTILUS_SCRIPT_SELECTED_FILE_PATHS'])

# make our data available to other applications
clipboard.store()
[/FONT]

 to your:

[FONT="Courier New"]~/.gnome2/nautilus-scripts/Copy Path[/FONT]

then:

[FONT="Courier New"] > chmod 744 '~/.gnome2/nautilus-scripts/Copy Path'[/FONT]

to make the file executable.

Force nautilus to restart:

[FONT="Courier New"]> nautilus -q[/FONT]

Is there a better way to do this?

---

### Post by sandipchitale on 2007-09-02
-

---

### Post by AZzKikR on 2007-09-03
Looks okay if you ask me. What does
```
os.environ['NAUTILUS_SCRIPT_SELECTED_FILE_PATHS']
```
return in Python?

---

### Post by sandipchitale on 2007-09-03
> **AZzKikR said:**
> Looks okay if you ask me. What does
```
os.environ['NAUTILUS_SCRIPT_SELECTED_FILE_PATHS']
```
return in Python?

Nautilus passes the list of selected files in the environment variable NAUTILUS_SCRIPT_SELECTED_FILE_PATHS - each file full path separated by a newline. 
The above code extracts and return the value of that variable.

Here are the details of other variables that are passed in:

When a script is invoked, Nautilus sets a few environment variables that can be used by the script:

NAUTILUS_SCRIPT_SELECTED_FILE_PATHS:
    newline-delimited paths for selected files (only if local)
NAUTILUS_SCRIPT_SELECTED_URIS:
    newline-delimited URIs for selected files
NAUTILUS_SCRIPT_CURRENT_URI:
    current location
NAUTILUS_SCRIPT_WINDOW_GEOMETRY
    position and size of current window

The selected files can also be referred to with the more traditional "$@" and "$*" bash variables.

---

