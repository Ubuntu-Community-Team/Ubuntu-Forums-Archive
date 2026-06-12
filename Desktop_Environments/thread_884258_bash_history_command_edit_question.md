---
title: "bash history command edit question"
date: 2008-08-08
forum: Desktop Environments
---

### Post by wdelv on 2008-08-08
Hello,
[INDENT]Although I am new to Ubuntu/bash/Linux I have been using UNIX for about 20 years; the first seven with csh and the rest with ksh.
I have been trying to edit some of the commands in my history but can only seem to get the arrow, backspace and delete keys to work.
I am used to vi-type commands from my ksh days but can't seem to get it to function.
I've tried setting EDITOR and FCEDIT to different combinations of /usr/bin/vi and /bin/ed but can't seem to get into the command mode to move around the text of the recalled command.
I can get the command to come up in a vi session for editing and the command mode works well there.
But I wanted to do this on a single-line mode (just like I used to get when typing ESC-K in the ksh).
I am using Ubuntu's gnome terminal with bash, of course.
What am I missing?
[/INDENT]

---

### Post by ndbrown on 2008-08-08
Hello, I'm new to this forum, but have used bash in cygwin (a Linux emulation layer for Windows), and bash in Ubuntu.

In the menu at the top of your desktop, select
**System -> Preferences -> Main Menu**
Then under **Applications** in the **Menus** box, click on **Accessories**, and go down to **Terminal** and either double-right-click or left-click and select **Properties**.  You should get a little dialog, **Launcher Properties**.

In the **Command** field, enter the following: **gnome-terminal -x bash -o vi**

Please post a response to let me know if this works for you.  I worked in Korn shell in AIX myself, using vi mode.

good luck.

---

### Post by wdelv on 2008-08-08
Thanks, ndbrown.
[INDENT]
However, after making your suggested changes and opening a new terminal window, I have the same condition (i.e. no command-mode).
Running set +o tells me that the -o vi option is set.
[/INDENT]

---

### Post by ndbrown on 2008-08-09
Just gotten up and fed the cats... Did you press ESC first, when you're in the terminal on the command line?  I can't remember if that was necessary in ksh, but it is in bash.  Give it a try and let me know.

---

### Post by wdelv on 2008-08-09
Funny thing.
Pressing the ESC key does allow me to type just one command-mode character (such as b - to back up a word) but immediately returns to the insert-mode.
If I type ESC, again, I might be able to type one more command-mode character, and sometimes it just keeps me in insert-mode.

Am I even starting out correctly?
In ksh I would type ESC-k to repeat and edit the last command.
In bash I type UP ARROW to repeat the last command (ESC-k doesn't do anything in bash) and then type ESC-<some other command-mode character>.

This seems so basic!

---

### Post by wdelv on 2008-08-09
I resolved the issue!
I needed to execute set -o vi in my shell.
I can do this in my .profile.
You would think that the changes to the Launcher would have done it.

---

### Post by wdelv on 2008-08-09
Actually setting this in my .profile .bash_login or .bash_profile had no effect.
It was as if these files were getting ignored at startup.
However, adding the line:
[FONT="Courier New"]set editing-mode vi[/FONT]
to my .inputrc file did the trick.

---

### Post by ndbrown on 2008-08-09
I was away most of the day... I checked my ~/.bashrc and see nothing there setting mode.  I tried **set -o vi** on the command line and it makes no difference - I think you are supposed to ESC to enter vi mode, which is how my terminal behaves.  I have a ~/.profile, and it's pretty minimal.  I don't have a ~/.inputrc, but I am getting vi mode when pressing ESC.

---

