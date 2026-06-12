---
title: "Letter 'D' won't suddenly work in terminal"
date: 2006-01-05
forum: Desktop Environments
---

### Post by cws on 2006-01-05
I did a fresh installation of Breezy on a PC. On the same machine, I have succesfully ran Hoary/Breezy for over a year. 

Now after the installation I configured NFS, upgraded Firefox etc. and suddenly letter 'D' won't work anymore in a terminal (gnome-terminal / xterminal). It works properly in any other application, so it's not a hardware issue. Weird, huh? I've never had these kind of problems before.

It's getting difficult to do anything when I'm unable to use sudo. Does anyone have any idea what's going on here?

---

### Post by Imexius on 2006-01-05
download aterm, or some other xterm replacement terminal.

---

### Post by dcstar on 2006-01-05
[QUOTE=cws]I did a fresh installation of Breezy on a PC. On the same machine, I have succesfully ran Hoary/Breezy for over a year. 

Now after the installation I configured NFS, upgraded Firefox etc. and suddenly letter 'D' won't work anymore in a terminal (gnome-terminal / xterminal). It works properly in any other application, so it's not a hardware issue. Weird, huh? I've never had these kind of problems before.

It's getting difficult to do anything when I'm unable to use sudo. Does anyone have any idea what's going on here?[/QUOTE]
In your terminal Edit-Keyboard Shortcuts and find where you have accidentaly assigned something to "D", and then disable it..........

---

### Post by cws on 2006-01-07
[QUOTE=Imexius]download aterm, or some other xterm replacement terminal.[/QUOTE]

Won't work on aterm either.

[QUOTE=dcstar]In your terminal Edit-Keyboard Shortcuts and find where you have accidentaly assigned something to "D", and then disable it..........[/QUOTE]

I haven't made any keyboard shortcuts. 'D' works fine in a ssh screen, but not locally in terminal. I don't get it...

---

### Post by nsstringer on 2006-12-03
> **dcstar said:**
> In your terminal Edit-Keyboard Shortcuts and find where you have accidentaly assigned something to "D", and then disable it..........
I had this problem with the letter "t" and your advice fixed it - THANKS  It had gotten assigned to "paste".  No idea how or when that happened.

---

### Post by cfg on 2007-08-24
Hello.

All of a sudden, I just got the same problem.  No idea why.  I checked Keyboard Shortcuts, and there was nothing asigned to "d".

"stty -a" similarly does not show anything.

I can get "d" to appear in the terminal by typing control-v d, but I'd like to be able to use it normally.

Any ideas?  Did you ever resolve the issue?

Thanks!!
CFG

---

### Post by cfg on 2007-08-24
Incidentally, Terminal -> reset and clear doesn't help, nor does rebooting.
Thoughts?

---

### Post by Rax on 2007-09-03
I am having this same issue.  It is driving me nuts because I cannot type in "sudo" to be able to edit or do anything as the superuser.  AHH!  Are there any other ideas out there??

---

### Post by cfg on 2007-09-05
Hey,

I have fixed it, sort of.  I still have no idea why it stopped working, which is irritating, but I was able to get 'd' to work again.

First, type:
bind -p

If, like me, something is wrong, the results should skip over the letter d, like:
[snip]
"a": self-insert
"b": self-insert
"c": self-insert
"e": self-insert
"f": self-insert
[snip]

Assuming that is the case, type:
bind d:self-insert

now try to type the letter 'd'.  It should work.  If it does, then add the above line to your .bashrc, and you should be good to go.

Like I said, I have no idea what caused this, and this little work-around is not pretty, but it gets the job done.

Good luck,
C.

---

### Post by Rax on 2007-09-05
What is this bind command?  It isn't in /usr/bin,  /usr/sbin, /bin, nor /sbin

---

### Post by Rax on 2007-09-06
Hmmm...  Just checked it on my work box of Ubuntu 7.04 and the bind command is there.  Perhaps this is part of the problem with my box at home...

---

### Post by tpetpefei on 2008-01-31
I had the exact same issue and this is how I fixed it.

To cause the issue I edited the **/etc/inputrc** trying to get rid of the annoying beep sounds that always occurred when tabbing to autocomplete an entry on the command line.  I uncommented the following line in the file "do not bell on tab-completion" thinking that this would prevent the beeping.

After changing this file and then rebooting the computer I was no longer able to type the lowercase letter 'd' on the terminal either on the machine or through ssh (using PuTTY).  However, in other applications in the gui I could still use the letter 'd' so this was not a hardware issue.

At first I was unable to copy the backup of inputrc I had made over the working inputrc file because both were owned by root, and without being able to type "sudo" on the command line there was nothing I could do.

However, you can do this without the need for sudo to allow you to fix the problem and get sudo back.  You need to copy the /etc/inputrc file to your home directory and create a ".inputrc" file that will be read and loaded when you log in to your terminal.  This will load your local settings and override the system settings enabling the use of 'd' on the terminal while logged in with your username on the shell.

In the shell you can type the following to copy the inputrc file to your home directory.

**[COLOR="#006400"]cp /etc/inputrc /home/{your user name}/.inputrc[/COLOR]**     [Notice the period in front]

The copy will be owned by you, so you can now edit the file through vim without the need for sudo as you now own the file and saving the edits will not require root permission.  Edit the file, and recomment (put the # back at the beginning of the line) the following line:

From this:

**[COLOR="Red"]do not bell on tab-completion[/COLOR]**

To this:

**[COLOR="DarkGreen"]# do not bell on tab-completion[/COLOR]**

Now save the file and logout of your terminal session.  When you log back in the local copy of .inputrc will be read and loaded, re-enabling the letter 'd'.  Now you have to sudo, and then edit the /etc/inputrc file and make the same fix there (re-comment out do not bell on tab-completion).

Once this is done you no longer need to have the local copy of .inputrc and you can change the name of this in your home directory to avoid any other conflicts should the /etc/inputrc be edited in the future.

cp /home/{your user name}/.inputrc /home/{your user name}/.inputrc.bak  [COLOR="Blue"](save it for a rainy day)[/COLOR]

As an interesting side note...if you create and fix your own local copy of .inputrc you will have 'd' available and can sudo.  However, if you "sudo -i" to enable an interactive root session you will find that 'd' is again inoperable as it is defaulting back to /etc/inputrc since you have changed users.  Once you have fixed /etc/inputrc than if you "sudo -i" you will find that 'd' works as both user and as root.

Hope this helps someone.  I found this out by doing one of those famous one line config file changes that seems so harmless and only shows it ugly head upon restarting the terminal or rebooting the system.  Luckily I was able to change back the only change I had made, and I made a backup of /etc/inputrc before modifying it...always do this...it's worth it to have lots of *.bak files in your /etc folder than having changed config files and no golden copies to revert back to.

Peace out

tpetpefei

---

