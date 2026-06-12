---
title: "Ubuntu Install reboot stall"
date: 2009-02-14
forum: General Help
---

### Post by dnslater on 2009-02-14
I am switching to Ubuntu for the first time from Windows XP on an old home computer and have encountered an install hitch.  My home computer is an older (7 years?) Dell 4500S Pentium 4, 1.8 Ghz with 384 mb of ram.  It has been riddled with viruses and issues over the years with abuse from kids, etc...  It doesn't run very smoothly and I was optimistic that Linux would breath new life in it, not to mention the benefits of wiping the hard drive and starting over.  Coworkers have given Ubuntu sparkling reviews.

I downloaded the .iso file from the Ubuntu website and created a boot disk.  I elected to install on the complete hard drive and do away with Windows XP.  I installed the program from the disk and went though the installation process smoothly, getting to the screen that asked me to restart to complete the installation.

The computer booted up and went through the Ubuntu logo screen then asked me to remove the boot disk.  I did this and hit enter and it went to the Dell Startup screen, then the screen went blank and showed "Grub Loading.." with just a few lines of additional text.  Then the screen went black with a white cursor that I can move around.  It stays on this screen and doesn't move forward.  I tried to hit the restart button and it beeps.  I unplugged to reboot, and it takes me to the same black screen and stops.  I tried to boot up in recovery mode and did a system check with no issues.  I then went ahead with the boot and back to the same black screen.

Frustrated, I tried to reinstall with the same results.  I searched the forum briefly but didn't encounter anyone else with this issue.  Any thoughts here?

Thank You,

Nick

---

### Post by dnslater on 2009-02-14
Update, still nothing, I tried some of the utilities under the recovery mode menu and now it sometimes freezes on an offwhite screen.  I may try to download openSUSE instead if I can't find an answer on this forum.  I took an online test and it recomended openSUSE #1 and Ubuntu #2.

---

### Post by geirha on 2009-02-14
When you are on the black screen with the cursor, does anything happen if you hit ctrl+alt+f1 ?

EDIT: Oh and another thing to try, when GRUB shows up, hit Esc to see the menu (if it is hidden), select the first entry and hit **e**, then select the line starting with kernel, and hit **e**. Remove the two words quiet and splash from the end of the line, hit enter, then **b** to boot. Any change?

---

### Post by dnslater on 2009-02-14
I tried this and it went to a black screen full of lines of text messages. (not to be too technical).  It freezes here.

---

### Post by geirha on 2009-02-14
What does the last few lines of text say?

---

### Post by dnslater on 2009-02-14
> **geirha said:**
> When you are on the black screen with the cursor, does anything happen if you hit ctrl+alt+f1 ?

EDIT: Oh and another thing to try, when GRUB shows up, hit Esc to see the menu (if it is hidden), select the first entry and hit **e**, then select the line starting with kernel, and hit **e**. Remove the two words quiet and splash from the end of the line, hit enter, then **b** to boot. Any change?

Just tried your second idea and it went through several pages of scrolling text, got my hopes up, then back to the stalled black screen with cursor.

---

### Post by dnslater on 2009-02-14
> **geirha said:**
> What does the last few lines of text say?

I just tried this again (hitting ctrl-alt-f1 during black screen)
It scrolled some text then was a command line asking for my username then password.  I typed them in and now there is a prompt that says dnslater@delllinux:~$

dnslater is my login and delllinux is the maching.  What should I type?

---

### Post by geirha on 2009-02-14
That means your ubuntu starts, but the graphical part (xorg) does not start for some reason. Try running ```
startx
``` What happens?

---

### Post by dnslater on 2009-02-14
> **geirha said:**
> That means your ubuntu starts, but the graphical part (xorg) does not start for some reason. Try running ```
startx
``` What happens?

I get the text:

Fatal Server Error:
Server is already active for display 0
   if this server is no longer running, remove /tmp/.xo-lock and start again

---

### Post by geirha on 2009-02-14
Hm. It's saying X is already running ... Cycle through all displays from F7 and up by hitting Ctrl+Alt+F7, Ctrl+Alt+F8, Ctrl+Alt+F9, etc. Do you get a graphical login screen on any of them?

---

### Post by dnslater on 2009-02-14
> **geirha said:**
> Hm. It's saying X is already running ... Cycle through all displays from F7 and up by hitting Ctrl+Alt+F7, Ctrl+Alt+F8, Ctrl+Alt+F9, etc. Do you get a graphical login screen on any of them?

Ctrl+Alt+F7 sent me to a brown muddy image, but no login.  Just the cursor which I can move..

---

### Post by rhcm123 on 2009-02-14
> **dnslater said:**
> I get the text:

Fatal Server Error:
Server is already active for display 0
   if this server is no longer running, remove /tmp/.xo-lock and start again

well, that means that the Xserver is hung somewhere along in the boot process. This is probably because your computer dosent simply have the power behind it to run both GNOME and Xserver at the same time. (read: needs moar RAM).

There are several things you can do:
1. Install xubuntu. A lighter-on-the-resources ubuntu designed for older machines (like yours). Running it on my sister's old P3 with no problems. Uses xfce instead of gnome.
2. Buy more RAM. It might (then again, might not) get the machine running.
3. Install ubuntu: server edition. That may sound complicated, but the only real difference from the desktop edition is that it
      A. Has no desktop enviroment (all command-line based)
      B. Comes with a few extra packages designed for servers.
After installing this, you can run the following command:
```
sudo apt-get install xfce
```
to get xfce and the asociated required packages
or, if you wanna try gnome again
```
sudo apt-get install ubuntu-desktop
```

hope this helps!

---

### Post by rhcm123 on 2009-02-14
> **dnslater said:**
> Ctrl+Alt+F7 sent me to a brown muddy image, but no login.  Just the cursor which I can move..

hmm... you said you have a command line on one of the screens?
type this:
```
sudo gdm
```
this should ask you for your password, then start the graphical login system

---

### Post by dnslater on 2009-02-14
> **rhcm123 said:**
> well, that means that the Xserver is hung somewhere along in the boot process. This is probably because your computer dosent simply have the power behind it to run both GNOME and Xserver at the same time. (read: needs moar RAM).

There are several things you can do:
1. Install xubuntu. A lighter-on-the-resources ubuntu designed for older machines (like yours). Running it on my sister's old P3 with no problems. Uses xfce instead of gnome.
2. Buy more RAM. It might (then again, might not) get the machine running.
3. Install ubuntu: server edition. That may sound complicated, but the only real difference from the desktop edition is that it
      A. Has no desktop enviroment (all command-line based)
      B. Comes with a few extra packages designed for servers.
After installing this, you can run the following command:
```
sudo apt-get install xfce
```
to get xfce and the asociated required packages
or, if you wanna try gnome again
```
sudo apt-get install ubuntu-desktop
```

hope this helps!

Thanks for all your help,  I had hoped 384 mb would be enough on a P4.  I may try opensus first.

---

### Post by dnslater on 2009-02-14
I did try the memory text under the recovery mode and it said I was ok.... not sure what that means however.

---

### Post by rhcm123 on 2009-02-14
> **dnslater said:**
> Thanks for all your help,  I had hoped 384 mb would be enough on a P4.  I may try opensus first.

It should... according to the ubuntu site ([https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")) you meet the minimum requirements

instead of openSUZE, try the moar user frendly xubuntu. it's still free, and comes with this handy support community. Looks nice too. (i never liked the look of SUZE. I didn't really like xfce, but my sister did, so... :) )


EDIT: I just saw your post about the memory test. This dosent mean that you have enough memory to run linux, it just means that your memory is not damaged.

---

