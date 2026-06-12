---
title: "[SOLVED] how to start destop 3d effects?"
date: 2008-12-04
forum: General Help
---

### Post by lidengdeng on 2008-12-04
Hi, I installed Ubuntu 8.04 a month ago. But I don't how to start 3d effects.

Any guideline for it?  Thanks.

---

### Post by glotz on 2008-12-04
Hi there! Right click the desktop > change background > visual effects and select how much bling you'd like.

There's a nice package to tune the compiz parameters called compizconfig-settings-manager in the universe repo.

---

### Post by Forlong on 2008-12-04
If it doesn't work (Desktop effects could not be enabled), go here: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by eternalnewbee on 2008-12-04
> There's a nice package to tune the compiz parameters called compizconfig-settings-manager in the universe repo.
Sorry for the intrusion, but as the OP is fairly new, it might be better to give more details. Like: Go to **Main Menu > System > Administration > Synaptic Package Manager** and search for **compizconfig settings manager**.
(No disrespect meant, glotz).

---

### Post by glotz on 2008-12-04
I was just being lazy, you're probably right. :D

---

### Post by eternalnewbee on 2008-12-04
> Hi, I installed Ubuntu 8.04 a month ago. But I don't how to start 3d effects.

Any guideline for it? Thanks.
Hi lidengdeng, and welcome to the Ubuntu Community.
It's very helpful, to people viewing your post, to mention your system specifications.
If you don't know where to find information about your hardware, you could go to: Main Menu > Add/Remove Applications, and search for **Sysinfo**.
After finishing the installation, you can find it under **Main Menu > System Tools**.
Of course the fastest way to find out what your system specs are, is through the terminal, but I don't know the command.
Good luck.

---

### Post by eternalnewbee on 2008-12-04
> I was just being lazy, you're probably right
Who can blame you? You must be one of the first members here):P

---

### Post by gabril on 2008-12-04
bah... 

open xterm and type! 

$sudo aptitude install compizfusion compizconfig-settings-manager

menu -> settings and there it is! Now you have to change your windowmanager to compiz

this is easyest done with just adding it to autostart or so that you can change whenever you feel!

$ sudo aptitude install compizicon

should do the trick!

Its in the same place menu -> settings and you see the icon!

This is a newbie forum, ops please respect this! 

Hope this helped!

---

### Post by eternalnewbee on 2008-12-04
Nice attitude...
> bah... 
> This is a newbie forum, ops please respect this!

---

### Post by lidengdeng on 2008-12-04
Thanks guys.
You are so kindly.
1). Right click the desktop > change background > visual effects and select how much bling you'd like.
I try this, but it does not work (Desktop effects could not be enabled). If it does not work, does that mean I could not enable the 3d effects on my pc?
2). You can use Compiz-Check to provide necessary info when asking for help!
My check output is OK for all the checked items.
3).Main Menu > System Tools
I installed the tool sysinfo, I list some of the items:
Realse: Ubuntu 8.04 (hardy)
GNOME: 2.22.2
Kernel: 2.6.24-19-generic
Graphic card: VGA compatible controller
Memory total: 3042 Mib

4).There's a nice package to tune the compiz parameters called compizconfig-settings-manager in the universe repo.
Yes, I can run the "Advanced Desktop Effects Settings" dialog. But after I selected items, including 3D windows, Desktop Cube, etc., there is no any change to my desktop. What items should I select?

Thanks very much!

---

### Post by lidengdeng on 2008-12-04
Yeah. I am a newbie to Ubuntu. The situation would be better If I knew it earlier.

---

### Post by coskierken on 2008-12-04
What are the specs on the system you are trying it on?  Look in the System/Admin/Hardware Drivers and see what, if any restricted drivers are loading and if they are enabled.  
Some on-board video does not like desktop effects very much.  I recently put it on an old P4 intel board and it was really screwed up.  I just did an install of XUbuntu on that system and I don't have problems.  On my laptop, I have an ATI X1700 and it does it pretty well.  It is frustating, though.  Just take it one step at a time.  Remember, 3D effects is memory HOG.  Also, you must turn them off to watch a DVD (mplayer,VLC, etc).

---

### Post by glotz on 2008-12-04
Open a terminal and input

**compiz --replace &**

Any clues?

---

### Post by Forlong on 2008-12-04
Please post the full output of Compiz-Check as well as the output of ```
compiz
``` in a terminal -- and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by lidengdeng on 2008-12-04
> **coskierken said:**
> What are the specs on the system you are trying it on?  Look in the System/Admin/Hardware Drivers and see what, if any restricted drivers are loading and if they are enabled.  
Some on-board video does not like desktop effects very much.  I recently put it on an old P4 intel board and it was really screwed up.  I just did an install of XUbuntu on that system and I don't have problems.  On my laptop, I have an ATI X1700 and it does it pretty well.  It is frustating, though.  Just take it one step at a time.  Remember, 3D effects is memory HOG.  Also, you must turn them off to watch a DVD (mplayer,VLC, etc).

Thanks, after activating the ATI Graphic driver in System/Admin/Hardware, then the 3d effects finally show.

---

### Post by eternalnewbee on 2008-12-04
Glad your problem is solved. Remember, every time a thread's problem is solved to mark it so, under Thread Tools, at the top of this page.
Have fun with the 3D effects:p
(Btw, take it easy on the thank yous. Once or twice is enough)

---

