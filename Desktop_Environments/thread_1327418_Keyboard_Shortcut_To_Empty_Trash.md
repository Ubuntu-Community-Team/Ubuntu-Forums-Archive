---
title: "Keyboard Shortcut To Empty Trash"
date: 2009-11-15
forum: Desktop Environments
---

### Post by Cygnia on 2009-11-15
Greetings, I'm trying to create a keyboard shortcut to empty the trash in Gnome on Karmic. I know that I can use the terminal to execute the following command successfully:

rm -rf /home/username/.local/share/Trash/*

Oddly though, the same command will not work when entered into the Keyboard Shortcuts preference pane. As part of my troubleshooting I tried to enter the above command into the Alt-F2 command dialogue, but it won't work there either. Is this a bug in Gnome? I know it's kind of a silly niggle for a Sunday, but I'm just curious why it won't work. Thanks for reading.

---

### Post by aysiu on 2009-11-16
Not sure why that's not working.

Do you get the same result if you run it as a bash script?

**Step 1**
Open a new text file for the script by pasting this command in the terminal: ```
gksudo gedit /usr/local/bin/emptytrash
```

**Step 2**
In the new text editor window, paste in ```
#!/bin/bash
rm -rf /home/username/.local/share/Trash/*
``` then save and exit

**Step 3**
Make the script executable by pasting this command in the terminal ```
sudo chmod +x /usr/local/bin/emptytrash
```

**Step 4**
Try running the command ```
emptytrash
``` to see if it works.

**Step 5**
Try using the command ```
emptytrash
``` as a keyboard shortcut.

---

### Post by cipricus on 2012-03-17
maybe when that not working is because the path to folder to be emptied is different - see [here ]("http://ubuntuforums.org/showthread.php?t=812712")

---

### Post by WonderWoofy on 2012-04-14
I know this post is a bit old, but the information contained is still valid.  So, just a thought, but would it not be better to use this command:

rm -rf /home/$USER/.local/share/Trash/*

That way the script can then be used to create a script for an logged on user, yeah?

---

### Post by markbl on 2012-04-14
> **WonderWoofy said:**
> I know this post is a bit old, but the information contained is still valid.  So, just a thought, but would it not be better to use this command:

rm -rf /home/$USER/.local/share/Trash/*

That way the script can then be used to create a script for an logged on user, yeah?
Yes. rm -rf $HOME/.local/share/Trash/* is better still. But these commands so far don't delete dotfiles in Trash (files or dirs starting with a dot). So the following command is better:
```

find $HOME/.local/share/Trash -mindepth 1 -delete

```

---

