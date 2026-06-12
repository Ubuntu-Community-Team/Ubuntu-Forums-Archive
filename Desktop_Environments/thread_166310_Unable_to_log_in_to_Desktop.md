---
title: "Unable to log in to Desktop"
date: 2006-04-26
forum: Desktop Environments
---

### Post by hermit on 2006-04-26
I have a dual-boot setup running Ubuntu 5.10 Breezy Badger 5.10. with Gnome as my desktop manager. Suddenly, after months of going through all the problems of getting most of the pieces of the puzzle working, I can now no longer log in. the message which I get after entering my username and password is as follows (computer is Clearsky and my name is yd):

Message after boot up following login attempt:

"!Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem."

pressing on the dialogue button brought up a log which read:
(~/. session-errors file)
"/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running /usr/bin/X11/sessreg -a -w /var/log/wtmp
/etc/gdm/Xsession: Beginning session setup . . .
_IceTransTransNoListen: unable to find transport: tcp
_IceTrans smkdir:Error euid != 0,directory /dev/x will not be created
_IceTrans smkdir:Error Cannot create /dev/x
_IceTransPT OpenSever mkdir(/dev/x) failed, error=13
_IceTransOpen transport open failed for pts/Clearsky:
_IceTransMakeAll COTSServerListeners: failed to open listener for pts

[here I've skipped a number of similar "_IceTrans" lines which ended the following:]
		Protocol is not supported by a SCO connection on . . .
				failed for sco/Clearsky:

[final line was:]
**(gnome-session:9092): Warning **: Unable to read ICE authority file:
					/home/yd/.Iceauthority

~~~~~~~~~~~~~~~~~~~
When trying to use KDE rather than Gnome:
"The following installation problem was detected while trying to start KDE:
	No write access to '/home/yd/ICEauthority'
KDE is unable to start."

then a pop up after clicking on the okay button:
"Could not start ksnserver. Check your installation."
~~~~~~~~~~~~~~~

My computer is a Dell Latitude D810 with a gig of ram and an ATI Radeon x600 video card

Prior to this, my final login I used a GUI to change the appearance of the desktop and also transfered my TTF fonts from the doze side over to my Linux setup.

If anyone can suggest a (hopefully simple) fix to help I would much appreciate it as doing a complete re-install would of course be exasperating.

thank you for any help,
hermit

---

### Post by frodon on 2006-04-26
Try a : ```
sudo chmod 777 /home/yd/.Iceauthority
```It may work.

You can use virtual terminal to do that (Ctrl+Alt+F1 to go to the virtual term and Ctrl+Alt+F7 to get back to the login screen)

---

### Post by hermit on 2006-04-26
When I use a virtual terminal and enter:
"sudo chmod 777 /home/yd/.Iceauthority"

the message returned is:
chmod: cannot access '/home/yd/.Iceauthority' No such file or directory

I fear that my installation is now partially trashed. Especially the "apt-get" system seems to be broken.

hermit

---

### Post by frodon on 2006-04-26
Don't worry i already got this problem several times, you just need to chmod your iceauthority file, the command return that because i should have made a typo with the name of the file. 
It should be : ```
sudo chmod 777 /home/yd/.ICEauthority
```

---

### Post by hermit on 2006-04-26
Frodon,
I owe you one. Big time.
Thank you for your patience and insightful suggestion. It was right on the money! You not only saved my installation but the three months of time it took me to build it up despite many difficulties.


hermit

---

### Post by hermit on 2006-04-26
Frodon,
I owe you one. Big time.
Thank you for your patience and insightful suggestion. It was right on the money! You not only saved my installation but the three months of time it took me to build it up despite many difficulties.

your compassion is very much appreciated,

hermit

---

