---
title: "KDE 3.5.3 broken screensaver - FIX HERE"
date: 2006-06-18
forum: Desktop Environments
---

### Post by arizonagroovejet on 2006-06-18
There a bunch of threads on here about the screensavers in KDE 3.5.3 not working.

I missed not having a screensaver so much that I decided to try and get it working using the latest KDE source. Somewhat suprisingly I managed it.

You can read all about it and grab the flies to hopefully fix it on your system at

[http://megaflexdestiny.net/bits/kde353screensaverfix/](http://megaflexdestiny.net/bits/kde353screensaverfix/)

---

### Post by berserker on 2006-06-24
Thank you for this.  It worked for me.

---

### Post by Lil_Eagle on 2006-06-26
Great for the 32 bit users, but is there an easy fix for 64 bit users?

---

### Post by forlau on 2006-06-26
For me it helped to ENABLE the energy saving option in the display settings.

---

### Post by Rastareefer on 2006-06-26
Hi, Thanks for making the fix which must have taken you a while to do.

I am new to Linux after jumping off the XP platform.
After downloading the file and trying to drag and drop it into the mentioned folder, I geta message "Access denied to /usr/lib/libkdeinit_kdesktop.so" and cancel is the only option.
 
I am not sure how to access permission to overwrite this file with the one downloaded.](*,)

---

### Post by Neo Ex on 2006-06-26
You can do this from a terminal:
```
sudo cp libkdeinit_kdesktop.so /usr/lib/libkdeinit_kdesktop.so
```
You must be in the directory where libkdeinit_kdesktop.so lives.
If you prefer the copy-paste way, you can use
```
kdesu konqueror
```
but remember that it's not a great idea launching programs by root when not necessary, so, be careful!

---

### Post by Rastareefer on 2006-06-26
Wow...Thanks for the quick reply.

I opened teminal and pasted the command but just got this back.

------------------------------------------------------------------------------------------------------
steve@AMD:/usr/lib$ sudo cp libkdeinit_kdesktop.so /usr/lib/libkdeinit_kdesktop.so
Password:
cp: `libkdeinit_kdesktop.so' and `/usr/lib/libkdeinit_kdesktop.so' are the same file
steve@AMD:/usr/lib$
------------------------------------------------------------------------------------------------------

Do I need to try the second command?

---

### Post by Neo Ex on 2006-06-26
Ehm... you have to download the libkdeinit_kdesktop.so file from that site and you put it, for example, in your home.
You must run that command not from /usr/lib, but from your home ;)

---

### Post by Rastareefer on 2006-06-26
I did download the file and ran the command.

The second command seems to have worked but the screen saver still refuses to start even after a reboot.

---

### Post by Rastareefer on 2006-06-26
AH, perhaps I was not in the home directory when I ran it.

Just tried it again in the "Home" directory but am getting Signal 11 errors.

---

### Post by Rastareefer on 2006-06-26
I'm afraid either because of my limited knowledge the fix doesn't work or perhaps the problem is not fixing due to the ATI Radeon 9550 card.

Will this get fixed in some kind of update or will I need to find another installation of Kubuntu? This problem seems to be in all the major distros so I guess I am out of luck.

PS:  Sorry for the confusion as to how to attempt to install the fix but as I mentioned I have only recently switched to Linux and my head is still spinning.

It may be an idea to post specific information for newbies on how to use the fix step by step.

Thanks for the help.

---

### Post by Lil_Eagle on 2006-06-27
There is now a 64-bit version also available!

[http://megaflexdestiny.net/bits/kde353screensaverfix/](http://megaflexdestiny.net/bits/kde353screensaverfix/)

I think this is such an important issue that I created a [HowTo]("http://www.ubuntuforums.org/showthread.php?t=204582")

---

### Post by Rastareefer on 2006-06-27
Thanks.......:-D :-D :-D :-D :-D :-D :-D

---

### Post by rubengs on 2006-09-13
I have the same problem but I'm running KDE 3.5.4 so no fix   for me.

---

### Post by Dr. Falken on 2006-09-22
> **rubengs said:**
> I have the same problem but I'm running KDE 3.5.4 so no fix   for me.

Did you checked that you have kde 3.5.4 installed??? (chequeaste tener instalado kde 3.5.4?)

In my case, i've updated to kde 3.5.4 but kscreensaver put a black screen insted of a screensaver... Screensavers works fine when i test them, and when i block the screen.


Suggestions to check???


El doc

---

### Post by someguyouknow on 2006-09-22
[http://kubuntuforums.net/forums/index.php?topic=8754.0](http://kubuntuforums.net/forums/index.php?topic=8754.0)
that is for 3.5.4

---

### Post by MrChips on 2006-09-27
Do the fixes work for me?

Yeah, to some extent.  The power saver has to be enabled for the screensaver to kick on.  But when it's time for the monitor to power down you get the black screen.  This is what others are getting as a screensaver when they don't enable power saving.

I think the problem goes beyond the screensaver fix.  The X installation was a real pain in both KDE and Gnome distros.  What happened? 

Man, I really like KDE but my monitor can't be left to burn for it.:-?

---

### Post by someguyouknow on 2006-09-27
did you try the one i posted?
it has worked for me and numerous others...
i havent tested the other one...

---

### Post by MrChips on 2006-09-27
> **someguyouknow said:**
> did you try the one i posted?

Yes, I guess the difference is yours works without power saving having to be enabled.  But still I get the black screen when the monitor is supposed to shut off.  It could just be my hardware config.  I have seen that this distro version wasn't very supportive of nvidia display cards.

---

### Post by someguyouknow on 2006-09-27
hmmm...
not sure then...
sorry i couldnt help...

---

### Post by Dr. Falken on 2006-09-28
> **someguyouknow said:**
> [http://kubuntuforums.net/forums/index.php?topic=8754.0](http://kubuntuforums.net/forums/index.php?topic=8754.0)
that is for 3.5.4
thanx!!! now it works!


El doc

---

