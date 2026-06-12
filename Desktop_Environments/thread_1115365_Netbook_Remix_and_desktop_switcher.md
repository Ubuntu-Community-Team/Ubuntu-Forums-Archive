---
title: "Netbook Remix and desktop switcher"
date: 2009-04-03
forum: Desktop Environments
---

### Post by Phospholipid on 2009-04-03
Hi there all.
Quite the issue on my laptop right now.

Today I installed Ibex (via liveUSB) onto my Dell mini 9. 
I then went for netbook remix (UNR) using apt-get to install the 7 packages required to implement the UNR desktop and other workings. I restarted, ran with UNR, and generally quite liked it but I can see times when I would rather not have it on. I also removed Maximus from the session as I didn't like every window I open going fullscreen as soon as I run it. 
**heres where it goes wrong**
I installed the package "desktop-switcher" and used the switcher to take me into classic mode. This worked fine. When I switched back to UNR mode I had lost my Panel. Without a panel present I don't know how to make a new panel. 

Any help would be much appreciated,
Thanks in advance,
Phospho

---

### Post by Phospholipid on 2009-04-04
I have fixed it now! Heres my solution.

I got stuck in an empty desktop without alt+F2 working so I was unable to open a terminal. 
I right-clicked - made a launcher for xterm then run that from the desktop icon now created. 
*I used xterm because terminal gave me an error message*
I tried killall gnome-panel which told me that the process wasn't running. 
I then tried gnome-panel witch funnily enough gave me a panel so I used the menu to get me into UNR where I would not require the panel if it was lost again.

*persistant fix*
I added gnome-panel to my session because on reboot the panel was still missing. 

Fixed. 

Hope somone finds this useful as noone seemed to want to help me out with it

---

### Post by hamishaus on 2009-04-05
Phospholipid, you rock!!!

I had the same problem, and used your fix. Works like a charm! Thanks!

Hamish

---

### Post by sabme on 2009-04-05
I found your comments very helpful!

I hope some one fixes this bug with gnome-panel not starting

---

### Post by ahbart on 2009-04-15
Hi, I just had the same issue and found a solution myself, removing .gnome2, .config and .gconf. You might want to confirm this bug I created at lauchnpad: [link](https://bugs.launchpad.net/netbook-remix-launcher/+bug/361625)

---

### Post by njpatel on 2009-04-16
Yes, this is a bug in desktop-switcher which I'm trying frantically to fix and get an SRU for. Please find more information on how to properly fix your problem at an eariler post of mine:

[http://ubuntuforums.org/showpost.php?p=7081942&postcount=8](http://ubuntuforums.org/showpost.php?p=7081942&postcount=8)

You'll also find a bug-link and that contains some (hopefully) fixed packages, on which I would appreciate some testing.

Thanks and hopefully that works for you.

Neil

---

### Post by boom2k1 on 2009-04-25
Thanks for your help!

Unfortunately, this bug still exists in Ubuntu 9.04 UNR after I used the preinstalled mode switcher to switch to the full mode. 

I think this bug will be run across so frequently by new Ubuntu users that it deserves high fixing priority!
 - a more visible way to help users to solve this problem before the bug will finally be fixed in a later release would be very helpful!

---

### Post by landtodd on 2009-04-28
With a fresh install of 9.04 UNR (on Acer Aspire One AOA-150):

I switched from the UNR interface to the "classic" desktop.  Left it there.  I booted into the "classic" desktop 3 or 4 times before the panels (top and bottom) disappeared.  Rebooted into the desktop a couple more times, and A) my icons on the desktop disappeared, and B) right mouse-click on the desktop stopped bringing up a menu.  The "classic" desktop interface was getting progressively worse.

I didn't have the fixes detailed here, so I reinstalled 9.04 UNR each of three times.  I finally stuck with the UNR interface, which has perfomed without a hitch.  

I don't like the UNR interface, but using it is a reasonable compromise to get as much hardware support for the AAO as exists in UNR.  (I came from an Everex Cloudbook, where I got everything working, but not at the same time!)

---

### Post by lucylettuce on 2009-04-30
I'm a complete newbie to Ubuntu.
I've installed Ubuntu on Acer Aspire One, and was playing around with the desktop switcher. I wanted to see what the classic Ubuntu was like, then decided to switch it back. I managed to switch back, but now the launcher window is too small, and I cant work out a way to resize it. When I open any program, I lose the small cross at the right hand corner to close it down. I can't view my account settings in Thunderbird. 
Is there an easy anyway of getting the original sized windows back?

---

### Post by landtodd on 2009-05-08
Lucylettuce,
Did you try njpatel's fix at [http://ubuntuforums.org/showpost.php...42&postcount=8](http://ubuntuforums.org/showpost.php...42&postcount=8) ?

I would like to know whether or not that works for you.

---

### Post by tdc204 on 2009-06-19
* I'm ultra-n00b*

I think I'm having the same problem.  I'm running 9.04 remix (ASUS 1008 ) and i used the desktop switcher to get into desktop mode.  Then I rebooted.  Now all i see is a desktop with some icons on it.  I cannot make heads-or-tails of how to implement any of the fixes suggested here.

---

### Post by tdc204 on 2009-06-19
I found some other fixes that might work for you.
[http://mydellmini.com/forum/beginners-questions/8058-ubuntu-9-x-only-see-desktop-icons.html](http://mydellmini.com/forum/beginners-questions/8058-ubuntu-9-x-only-see-desktop-icons.html)

this one worked for me
"Try logging in to your blank Gnome session. Then right-click on the desktop and choose "Create Launcher". Input "gnome-terminal" in the "command" field. When you finish, you should have an icon to launch a terminal on the desktop.

Launch a terminal, then input "gnome-panel" to try to manually start the panel application."

---

### Post by takumidesh on 2010-03-19
I have had this same problem on my eee pc on 701. The only problem is my right click menu does not work. None of the alt and ctrl shortcuts work. Is there any other workaround for this? Thanks.

---

