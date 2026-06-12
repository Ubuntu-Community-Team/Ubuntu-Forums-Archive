---
title: "Terminal utility of sorts?"
date: 2009-03-15
forum: General Help
---

### Post by r1ch on 2009-03-15
Hi there,

bit of an odd question really... I've been learning to use terminal commands bit by bit and am building up quite a collection which I copy and paste from a text file when I need them. 
Does anyone know of a simple utility to store terminal commands that you use regularly so they can be clicked to run? I know I can put some on the Ubuntu panels which I do occasionally but I certainly wouldn't have enough room for all of them.

Thankyou.

---

### Post by x33a on 2009-03-15
you can use tab completion to shorten the typing work, i.e., just press tab after typing a few characters.

e.g. fire<tab> will open firefox.

and the last 500 commands you type in the terminal are stored. you can access them with ctrl+r, type a few characters of the command and the terminal will try to complete it. you can access the command history through "history" command.

---

### Post by Dirjel on 2009-03-15
You could also stick a drawer (or a few drawers inside of a drawer) on your panel.  Might be nice for you, since you can sort of organize things.

---

### Post by unutbu on 2009-03-15
You could convert your commands into scripts. Then you could use the file browser as your GUI to access and run your commands:

Suppose you have a command like this
```

cp -r /home/r1ch/* /home/backup
```

If you'd also like to be able to click to run it, perhaps create a text file 
called ~/bin/cp-home.sh```


#!/bin/sh
cp -r /home/r1ch/* /home/backup
```

Make it executable:```

chmod 755 ~/bin/cp-home.sh
```

That's all it takes to turn a shell command into an script.

Then whenever you wish to run the command, just use your filebrowser (nautilus)
to navigate to ~/bin. Double-click the icon "cp-home.sh" and a dialog box will pop up.
Click "Run" to run it.

By doing this, you will also be able to run the script from the terminal.
Instead of typing 
```

cp -r /home/r1ch/* /home/backup
```

you could type
```

cp-home.sh
```

---

### Post by .Maleficus. on 2009-03-15
One thing you could do is create Bash aliases to shorten them.  Ie, I use abcde to rip music from CDs.  Example:
```
#Original command
abcde -o flac -d /dev/cdrom
#Bash alias in .bashrc
alias rip='abcde -o flac -d /dev/cdrom/'
#Run this in terminal
rip
```
Works fairly well.  I'm using dwm so I have like, 4 terminals open at any one time so double clicking an icon to run something that takes 3 letters to type isn't really intuitive, so take it with a grain of salt.

---

### Post by r1ch on 2009-03-15
Thanks for all the pointers everyone. Some nice ideas there so I'll have a play around and see how I get on.

Cheers.

---

