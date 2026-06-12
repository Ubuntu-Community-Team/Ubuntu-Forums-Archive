---
title: "Ubuntu won't open after using Mate Tweak tool and switcing to Compiz"
date: 2015-12-12
forum: Desktop Environments
---

### Post by bill23 on 2015-12-12
I have Ubuntu 15.10 (Mate) and I used the Mate Tweak tool and switched to Compiz, but it did not 'cycle' through back to the 'Tweak tool' page. I waited several minutes to give it plenty of time and then rebooted. The login screen showed up, I login. However instead of the Start Up Window, I am greeted by a screen with the Ubuntu/Mate icon and naught else.
 
 
 I would like to get back to where I was before I made the gross mistake of fooling around with Compiz. The problem is I can't get into Ubuntu to do anything. One option would be to reinstall Ubuntu, but there is an issue with that option. I have three other Linux distros besides Ubuntu on my PC, and Ubuntu 15.10 is the third one on the Grub Screen listing as: /dev/sda6. With Mageia 5 /dev/sda5 and PCLinuxOS /dev/sda7 on either side. The final distro is Manjaro /de/sda3, with /dev/sda1 as Swap and /devsda2 Extended.
 
 
 I do have about 160GB of available space on my PC, and theoretically, could use it to install 'Ubuntu' again. An option I am loathed to do unless I am left with no other options. I know I can use a Gparted Disc and delete /dev/sda6 (Ubuntu), but I have never tried to reinstall a distro between two distros before. Also using Gparted in such a way, I risk getting the "Grub Rescue" screen.
 
 
 Right now, I am running Mageia 5, to post this thread.
 
 
 Is there anything I can do after I have logged in to return to the default settings or when I am about to choose from the GrubScreen?

---

### Post by v3.xx on 2015-12-12
It sounds like you need to reset to [marco]("http://manpages.ubuntu.com/manpages/wily/man1/marco.1.html") from the console.  At the grub screen press:

Ctrl + Alt + F1

That will take you to console (tty).  You then need to login and run:
```
marco --display=:0 --replace
```
[http://askubuntu.com/questions/154112/how-do-i-disable-compiz-and-enable-metacity-with-the-command-line](http://askubuntu.com/questions/154112/how-do-i-disable-compiz-and-enable-metacity-with-the-command-line)
[http://ubuntuforums.org/showthread.php?t=1270527&p=7976092#post7976092](http://ubuntuforums.org/showthread.php?t=1270527&p=7976092#post7976092)

Another possible solution
[http://ubuntuforums.org/showthread.php?t=1344437&p=8430609#post8430609](http://ubuntuforums.org/showthread.php?t=1344437&p=8430609#post8430609)

---

### Post by bill23 on 2015-12-13
I did as you suggested and it did not work. I came up with this:

"Invalid MIT-Magic-Cookie-1
keywindow manager error
unable to open X display :0

Anyone know how to open 'X' display, so I can get back to the way it was prior to my screwing things up.


I am very discouraged by the apparent lack of assistance to my problem as it gets shunted out of sight out of mind.

12-26-15

With a suggestion from one, TxLonghorn, I installed Ubuntu again in the same partition where it had been before I screwed it up messing with what I did not know of. Now I can boot into Ubunt and I am staying away from Compiz.

---

