---
title: "Resolution issues"
date: 2009-01-05
forum: General Help
---

### Post by FaresH on 2009-01-05
I have the NVIDIA GeForce 8800 GTS and a 21 inch LCD CHIMEI CMV 221D.
The graphic card and the LCD work fine on windows. 

It all started a couple of days ago when the computer got shutdown due to an electric cut. ( The fault of my brother the genius ).

First Ubuntu didn't mount the 2 partitions I have. Which was ok...
Then the resolution went down to 640*480, and when I take it back to 1240*1040, the window grows but doesn't adjust it self to the monitor. For example, if I see the Application menu, I need to move the mouse to the right-end, so that the window slides right to see the shutdown button. But all this is gone, I didn't fix it. Now I get a black screen. When I restart the pc, I see the ubuntu loading, but the moment before the login screen must appear, the monitor gives me a "No input" message, and the screen goes black. 

I Can't get into ubuntu now, but I can get into the recovery mode. Any ideas how to solve this ?

---

### Post by arno1991 on 2009-01-05
I had the same problem also several times, I had some computers with standard VGA onboard video cards with that problem, a ATI X360 and an NVIDEA 6600Go (laptop). The problem occures when you try to install some software that tries to reconfigure your graphic card, or because a false setting, and so on.

You can install the graphic card again, but i think it will be easier to install the Gnome-desktop of ubuntu again. 
And if you need to install your graphic card, i advise to use EnvyNG (it is in the repositories!)

sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

i hope it works, else, i guess you need to reinstall the xserver? same as above

success

---

### Post by FaresH on 2009-01-05
I can do it from the recovery mode right ?

---

### Post by FaresH on 2009-01-05
I did it from the recovery mode... I Can not reinstall ubuntu-desktop after I remove it. An err occurs, something about fetching and authenticity. 

And I do not have the xserver installed.

---

### Post by FaresH on 2009-01-06
I solved the problem. Here is how I solved it...

The moment you get the Grub, choose the normal ubuntu mode.
After ubuntu loads, you will hear the sound of the welcome login window.
Press ctl + alt + f1, it will send you to terminal.

Step 1 : cd etc/X11/
Step 2 : sudo editor xorg.conf
Step 3 : add the following :

         Under the Server flags section

         BlankTime "0"
         StandbyTime "0"
         SuspendTime "0"
         OffTime "0"

         Under the Monitor section

         DPMS "false"

press ctl + x
it will ask you if you want to save what you have modified, enter the y key.

Then enter ctr + alt + del, this will restart the pc. And you are home free.

---

