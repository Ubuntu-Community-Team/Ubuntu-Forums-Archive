---
title: "Shortcut for backing up xorg.conf?"
date: 2009-04-04
forum: General Help
---

### Post by jamesclish on 2009-04-04
Hi all!

I'm getting a little tired of typing ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
``` every time I want to make a tweak in the file. (I know it's not compulsory, but if you knew how many times I've restored it...)

Anyway, I'm pretty new at all of this, and I've read about a thing called shell scripting (equivalent to Windows batch scripting?). I wondered whether it's possible to put the backup command into a "batch file" that was either clickable from the desktop or accessible with a single word in terminal (similar to how one can type "firefox" into the terminal.).

I hope that all makes sense.

Thanks in advance!

NB: I don't know if this thread belongs in the "Absolute Newbie Talk" section or not...

---

### Post by PhrankDaChickenGeek on 2009-04-04
Here's how to make an executable text file:
```
touch backup_xorg
chmod a+x backup_xorg
gedit backup_xorg
```

And put the following in the file (or whatever commands you want to run - Just make sure the '#!/bin/sh' line is there):
```
#!/bin/sh
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```

To run, you'll need to be in the same folder as the file, and type:
```
./backup_xorg
```

To run the command from any directory, copy the file to /usr/bin
```
sudo cp backup_xorg /usr/bin
```

---

### Post by VCoolio on 2009-04-04
too late :-)

---

### Post by jamesclish on 2009-04-04
Perfect! Thanks!

Erm... Any advice on how to mark this thread as solved, by any chance?

---

### Post by philinux on 2009-04-04
Just create a launcher, type=app in terminal, on your desktop. Easy peasy.

Copy your cp command in and job done.

---

### Post by CatKiller on 2009-04-04
> **jamesclish said:**
> Hi all!

I'm getting a little tired of typing ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
``` every time I want to make a tweak in the file. (I know it's not compulsory, but if you knew how many times I've restored it...)

I know it's not quite what you asked for, but I think a neater option is to use the shell's history. If you edit your /etc/inputrc to uncomment these lines

```
# alternate mappings for "page up" and "page down" to search the history
"\e[5~": history-search-backward
"\e[6~": history-search-forward
```

then you can start typing the start of your command, and then use PageUp and PageDown to complete the command with the previous commands that you've used that start the same way (similar to normal Tab-completion, but based on the commands that you've used). This will work for all commands, not just the one that you want to create this launcher for. I use this a lot, and feel quite crippled if I use someone else's computer that doesn't have the history-search enabled.

---

