---
title: "Remove individual xscreensavers from list?"
date: 2012-09-24
forum: Desktop Environments
---

### Post by c4c on 2012-09-24
[COLOR=black][FONT=Ubuntu][FONT=Times New Roman]I'm [newly] running Lubuntu 12.04, have installed XScreensaver 5.15 (28-Sep-2011) and then *removed* several screensavers that seem to be too much for the Pentium 4, and/or the 512 MB RAM and/or the graphics card I have. *Removing the actual screensavers wasn't a problem*. [As an aside - I'm really liking the whole Ubuntu 12.04 on older hardware experience with Lubuntu - it's really snappy and looks nice][/FONT][/FONT][/COLOR]

[COLOR=black][FONT=Ubuntu][FONT=Times New Roman]All of the xscreensavers I deleted, including some that seemed to have been listed by default (I believe they were there and greyed-out before I ever installed xscreensavers) are still listed under Preferences [/FONT][/FONT][/COLOR][COLOR=black][FONT=Wingdings][FONT=Wingdings]à[/FONT][/FONT][/COLOR][COLOR=black][FONT=Ubuntu][FONT=Times New Roman] Screensaver in the LXDE desktop. These screensavers are listed as “Not Installed.”[/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Ubuntu][FONT=Times New Roman]Apparently these screensavers are still selectable. If the cursor is left on them and/or they have been selected before the screensaver starts, I will get an error as they aren’t actually installed. These screensavers are also selectable by the “Random ScreenSaver” option/mode available from the drop-down menu under Preferences [/FONT][/FONT][/COLOR][COLOR=black][FONT=Wingdings][FONT=Wingdings]à[/FONT][/FONT][/COLOR][COLOR=black][FONT=Ubuntu][FONT=Times New Roman] Screensaver as some of the screensavers that no longer exist (or never did in some cases) in my install get selected by the system. I have to manually uncheck the boxes.[/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Ubuntu][FONT=Times New Roman]Thanks in advance to anyone who can tell me how to remove the *listing* of xscreensavers from the Preferences [/FONT][/FONT][/COLOR][COLOR=black][FONT=Wingdings][FONT=Wingdings]à[/FONT][/FONT][/COLOR][COLOR=black][FONT=Ubuntu][FONT=Times New Roman] Screensaver. [/FONT][/FONT][/COLOR]

---

### Post by squaregoldfish on 2012-09-24
You should have a .xscreensaver file in your home directory, that lists all the screensavers that your system thinks it has. Simply delete the lines corresponding to the savers you've deleted.

Steve.

---

### Post by c4c on 2012-09-24
Awesome! Thought it was something simple like that. Thanks! :P

---

### Post by c4c on 2012-09-26
Okay. First -this *was* solved. And second; my apologies for my apparent misunderstanding of the way the Screensaver Preferences on Lubuntu 12.04 are supposed to work. 

The file referenced above (.xscreensaver) by squaregoldfish is totally there, but is only supposed to disable individual xscreensavers at the user level. On Lubuntu, using leafpad instead of gedit, the command in LXTerminal would be: ```
gksudo leafpad ~/.xscreensaver
``` - What is supposed to be the *system-wide* defaults file (that feeds the .xscreensaver file it’s info) is found in /etc/X11/app-defaults/XScreenSaver-gl

The [xscreensaver man pages]("http://www.jwz.org/xscreensaver/man.html") (-duh) advises not to remove individual screensavers (as I had done) and not to remove their listings from the two files referenced above (which I had also done). To disable a particular xscreensaver; I was supposed to simply mark each one as *inactive*. This is like commenting them out, but placing a "-" at the beginning of their line in .xscreensaver for the user and XScreenSaver-gl for system-wide inactiveness.

I un-installed xscreensavers and again found the Preferences --> Screensaver (what the man page calls xscreensaver-demo) to be virtually devoid of selectable screensavers. Over 200 were listed, but all of them were again greyed-out/not installed. The “screensaver" only served to blacken the screen. *This is what I remembered with the default Lubuntu 12.04 install and was the reason I installed xscreensaver packages in the first place.*

I then re-installed the xscreensavers; ```
sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra
``` This still left me without the screensavers included in the xscreensaver-gl_5.15-2ubuntu1_amd64.deb package (listed [here]("http://pkgs.org/ubuntu-12.04/ubuntu-main-amd64/xscreensaver-gl_5.15-2ubuntu1_amd64.deb.html"))* - I would have made those screensavers inactive anyway.*

I then went about deactivating the other xscreensavers I didn’t feel this computer did well with - and a few more I found terribly ugly or distasteful. I am now almost back to where I started - I didn’t delete any screensavers off my system this time, but have 101 selected in “Random” mode - which I think is probably plenty.

---

