---
title: "Xubuntu 8.10 with Intel 830MG -&gt; graphic errors"
date: 2008-11-09
forum: Desktop Environments
---

### Post by Dumdideldum on 2008-11-09
I am running Xubuntu 8.10 (upgraded from 8.04) on a HP Omnibook 510 with integrated Intel 830MG video card.

Since the upgrade, I have severe graphic errors in X - especially when using Firefox.This is for sure no hardware defect, as I didnt see those problems within 8.04 or WinXP.

The graphic errors appear as misformed characters, blackened out characters and icons turning white or totally invisible. When switching to tty2 and going back to X (tty7), the graphic errors disappear mostly for a short period time till they turn back again - and mostly show the same misformed behavior - so I think this is memory related.

Any ideas ?

thx

Edit:
I cant add my Xorg.0.log as attachement as it exceeds the attachament size limit.

---

### Post by M.A.L.M. on 2008-12-03
I have the exact same problem with a new installation of Xubuntu 8.10 on an Acer TravelMate 260 that uses the same video card (Intel 830MG). I DO NOT have any sort of desktop effects enabled.

I normally use Ubuntu, but this is an old laptop: Pentium III-M 999MHz; 256MB RAM, 8 of which appear to be used by the integrated video subsystem. I thought I could "liberate" my friend's computer from the MS OS, but the results are not what I had hoped for. Sometimes it looks even slower now than with Windows XP. But these graphic errors are a no go; it makes the desktop unworkable and I don't want my friend to have such a bad first impression of Linux!

Also, pressing CTRL+ALT+F1 etc doesn't bring up the tty's...

I'll try installing Xubuntu 8.04.1 and see if it's any better.

---

### Post by molibden on 2008-12-12
I had the same problem while trying Xubuntu 8.10 on my Dell Latitude x200 (also with Intel 830MG). After having Xubuntu 8.04 installed, these problems disappeard and everything seems working fine.

---

### Post by stayrollin on 2008-12-16
Same issue. I am also on a Dell x200. 

Firefox's fonts become unreadable and I get tears on the desktop.

---

### Post by spirit59fr on 2008-12-20
Am having exactly the same problem with my Thinkpad X30 using i830MG. A real pain...

After reading several comments here and there, compiz is NOT the problem.

Any workaround possible or does it imply a complete fresh install of Ubuntu 8.04.1 for the moment ? (or is it possible to downgrade part - and which one - or the whole of the system - and then how ?)

Sorry, not of much help, I'm useless as soon as it has to do with under-the-hood issues.

---

### Post by druellan on 2008-12-20
A shoot in the dark, but you can try some of this: [http://ubuntuforums.org/showthread.php?p=6148867](http://ubuntuforums.org/showthread.php?p=6148867)
Its a totally different effect, but perhaps its related since this does not happens on Hardy either.

---

### Post by Nevyn on 2009-02-04
I had the exact same problem with my IBM X30 using Xubuntu and was just about to go back to 8.04, when I on a whim decided to test Gnome instead of the xfce environment. And look, **it worked!**

[SOLUTION]
Guided procedure as follows:
In your terminal (Applications->Accessories->Terminal) type 
```
sudo apt-get install gnome
```
Wait until the huge package is downloaded and installed.
Log off.
When viewing the logon screen, choose Session->GNOME
Log on as usual, end of procedure ;)

Now I'm not an advanced user so I don't know how well using gnome utilizes Xubuntu vs using regular ubuntu instead, but at least it solved the graphic issues, and I don't experience the computer to be slower.

---

### Post by jlabomb on 2009-04-27
I have the same problem with this video card in my HP Pavilion N5445. I am running XUbuntu but I did install GNOME and it is still an issue. GNOME is a lot better than XFCE was but after awhile it will become distorted. I just upgraded to Jaunty hoping it would fix it. Any new ideas on this?

---

### Post by spirit59fr on 2009-04-27
jlabomb => Please let us know how it goes with Jaunty...

---

### Post by jlabomb on 2009-04-27
Jaunty was no help. I am I right in thinking that 8.04 was working before the upgrade or was it an older version of ubuntu?

---

### Post by spirit59fr on 2009-04-28
Actually, I'm not sure it has to do with Ubuntu so much, rather with the version of Firefox.

Let's keep up !

---

### Post by jlabomb on 2009-04-28
The errors in my display are not limited to Firefox. They occur in the whole desktop environment in GNOME or XFCE.

---

### Post by spirit59fr on 2009-04-29
Fair enough, but could you check whether that happens at all if you don't launch Firefox in the first place. I mean, it could be that Firefox is the origin of the problem, altough the consequences can be seen beyond Firefox itself.

---

### Post by Newtothegame on 2009-05-03
Ok so I am dealing with the same issue and after trying and having to do a complete xorg rebuild I moved to the IRC. This led me to a few other sources and an Xorg.conf edit. 

I am going to post my issues and then the whole xorg.conf file. 

First issue was on my dell x200 the cursor would disappear when i adjusted brightness. The next issue was the blocky characters and artifacts displaying on the screen after some time.  This required me to add some text under the device section in xorg.

So what you need to do.This is for Xubuntu: Launch terminal> type (quotes removed) "sudo mousepad /etc/X11/xorg.conf" > hit enter > type password. This should launch an editable xorg file. Note the device section (this was the only place I made changes even though I am pasting the whole xorg file.) 

____________________________________________________________________________________

Section "Device"
	Identifier	"Configured Video Device"
	Option 		"HWCursor" "false" 
	Option		"SWCursor" "true"
	Option 		"MigrationHeuristic" "greedy"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
-----------------------------------------------------------------------------

So far this has worked for me. 

Now back to finals :P

---

### Post by jlabomb on 2009-05-06
Thank You Newtothegame that did it. Screen is as clear as a bell. The problem was also not caused by Firefox since it would occur without me launching it. Thanks Again.

---

### Post by afdoughty on 2009-05-19
> **Newtothegame said:**
> Ok so I am dealing with the same issue and after trying and having to do a complete xorg rebuild I moved to the IRC. This led me to a few other sources and an Xorg.conf edit. 

I am going to post my issues and then the whole xorg.conf file. 

First issue was on my dell x200 the cursor would disappear when i adjusted brightness. The next issue was the blocky characters and artifacts displaying on the screen after some time.  This required me to add some text under the device section in xorg.

So what you need to do.This is for Xubuntu: Launch terminal> type (quotes removed) "sudo mousepad /etc/X11/xorg.conf" > hit enter > type password. This should launch an editable xorg file. Note the device section (this was the only place I made changes even though I am pasting the whole xorg file.) 

____________________________________________________________________________________

Section "Device"
    Identifier    "Configured Video Device"
    Option         "HWCursor" "false" 
    Option        "SWCursor" "true"
    Option         "MigrationHeuristic" "greedy"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
-----------------------------------------------------------------------------

So far this has worked for me. 

Now back to finals :P


I have a Dell X200 with exactly the symptoms described in this thread and am a newbie to linux - loving the idea of no more Bill Gates but really struggling to get this all working.

When I tried to use your solution, for some reason launching from terminal would not allow me root access to the file and it could not be saved. So I saved a copy to the desktop and opened a file manager from the terminal and drag and dropped the file from the desktop to the etc/X11 folder and rebooted. It worked a treat. 

However, the next problem was firefox - the fonts there were still rendering very badly. I found a solution elsewhere based on changing a firefox setting (not a OS setting). 

Here's what I did:

In the firefox address bar type "about:config" [enter]
In the filter box type "dpi"
The settings for layout.css.dpi should appear in the list below
Change the value to '0' (zero) (right click on the number and select edit or change)
Restart firefox

 -- this forces firefox to use system font settings and it all looks much better.

Andrew

---

### Post by Newtothegame on 2009-05-31
Hmm thats odd. My orginial post fixed the firefox issue on my comp. 

Glad to know that it worked in part tho. 

Also isnt the dell x200 nice to carry about and zippy on Kubuntu :)

---

### Post by afdoughty on 2009-06-01
I certainly works better than XP. When I bought the machine it ran XP and Office well. However, it got slower and slower so I upgraded the memory and that helped for a bit. Despite religious disk and file maintenance it got unbearable.

I am now wondering why Linux can see/use the extra memory I bought. The system monitor only shows the root memory, not the extended memory (inserted in a port under the machine).

Also, can't get Wine to work with my copy of office .... keeps asking for the registration key even though its been put in already .....

---

