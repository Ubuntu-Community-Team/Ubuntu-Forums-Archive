---
title: "Nautilus Script for ccrypt"
date: 2006-09-18
forum: Desktop Environments
---

### Post by subiet on 2006-09-18
Can anyone please explain how to make a nautilus script for a small encryption/decryption utility call ccrypt.

the command for encryption is:
ccrypt -e "filename"

then in the terminal it asks for a key

similarly for decryption the command is 
ccrypt -d "filename"

---

### Post by Ramses de Norre on 2006-09-18
These scripts will open a terminal which will then ask the key, that's what you wanted, right? 
Copy them to files in .gnome2/nautilus-scripts/ and make them executable. (One script/file)```
#!/bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
for I in "$*"
do
    gnome-terminal -x ccrypt -e $I
    exit 0
done
```

```
#!/bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
for I in "$*"
do
    gnome-terminal -x ccrypt -d $I
    exit 0
done
```

---

### Post by subiet on 2006-09-18
it opens the terminal for input, but the file doesn't get encrypted

---

