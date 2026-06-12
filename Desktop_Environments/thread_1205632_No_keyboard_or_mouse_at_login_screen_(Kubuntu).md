---
title: "No keyboard or mouse at login screen (Kubuntu)"
date: 2009-07-06
forum: Desktop Environments
---

### Post by niawniaw on 2009-07-06
Hi all,

Im very new to Ubuntu and Linux environment in general. I installed 9-04 about month ago then the KDE interface abt 2 weeks ago. Everything was very fine until today. After i left the PC for 30 minutes and then came back, the screen was locked and asked me for username/pass as usual so i typed in and press Enter. To my surprise, it said that the login something doesnt work, I need to kill another process (which very unfortunately i didnt write down the name, sorry for my noobies @__@) in order to login again.
Since im new to ubuntu, i didnt know where to run the command to kill that process (it was a blank screen, after the screen saver gets actived and then deactived) so i tried to change session. It changed to login screen after i chose, but without any user name on the list. When i tried to type in my username/pass, it says samething like earlier when i came back after 30 minutes of inactivites. Hence i had no idea of what to do, so i restarted my PC, and there i go, after rebooting, no mouse or keyboard activities (even numLock button doesnt work). I cant type anything, i cant move the mouse, i cant chose anything, and of course still no user name on the list (im using KDE login screen with name browser).

Here are what i have done earlier today which might bring more information about this dilema =_=,,

-I was trying to get the USB support to work with VirtualBox (i put 1 line in the fstab file like in the help i found in internet)
-I use KDE interface, KDE login screen
-I activated the power saving in KDE, which makes the screen to turn off after 10 minutes and will ask for pass after waking up.

Other than that, everything i did today was normal.

Please help me to get Ubuntu alive again!!! ^_^,
Thanks in advance!

---

### Post by krazyd on 2009-07-06
Did you make a backup of the fstab?

---

### Post by niawniaw on 2009-07-06
> **krazyd said:**
> Did you make a backup of the fstab?
Thanks for the response!

No...i didnt :(
As i already stated, im very new with Linux. But could it be the reason since the whole thing happened while my PC was on all the time? I though if the change to fstab caused trouble, it should do right after i changed/saved it.

Ah, to add more info, when i turn on PC now and go into Ubuntu/kubuntu, the only thing that works is the power button. Sound and graphic however seems to be normal.


PS: can anyone tell me the name of the login manager in kubuntu? Maybe i should try to reinstall it? I can still boot to the netroot, just dont know any command L:>.

---

### Post by Monsieur Gonzalez on 2009-07-06
It's called kdm. If you can access the command line, try with sudo dpkg-reconfigure kdm.

---

### Post by niawniaw on 2009-07-06
> **Monsieur Gonzalez said:**
> It's called kdm. If you can access the command line, try with sudo dpkg-reconfigure kdm.
Thanks a lot! I will try this later today after work and will tell you if it works.

---

### Post by edvar on 2009-09-30
It just happened to me. Hal wasn't loading so I got no mouse, keyboard, sound or network available after I installed an upgrade to kernel 2.28.15.52 in Jaunty.

I tried several things but nothing worked then I realized the folder /etc/hal was empty!

I went to a Linux Mint Gloria VM I had installed on another computer and checked the contents of the folder. The folder structure is basically:

/etc/hal/fdi
/etc/hal/fdi/preprobe
/etc/hal/fdi/policy
/etc/hal/fdi/information

I recreated the folders on my Ubuntu Jaunty box and rebooted. After that I was back in business!

---

