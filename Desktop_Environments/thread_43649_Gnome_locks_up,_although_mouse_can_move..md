---
title: "Gnome locks up, although mouse can move."
date: 2005-06-22
forum: Desktop Environments
---

### Post by department27 on 2005-06-22
Hi,

Not sure if this is the right place to post this problem, but here goes.

Running hoary, 686 kernel, uptodate with patches. Have apps from backports aswell. Machine is a Dell D600. 

Now comes the problem. Every so often everything locks up. Keyboard, screen, but the mouse can be moved around the screen.

I have telnet enabled and can telnet to the machine. All background processes seem to work, i.e apache, samba, etc.

Once telneted in I can shutdown processes in init.d with the stop option. 

But when I try to stop gdm then machine locks up totally. I get kicked off telnet, mouse stops working.

I have checked the logs but there are no errors whatsoever.

The question is, has anybody else had this. And is there a way to troubleshoot what is causing the error once I have telneted in.


Thanks in advance

---

### Post by TheRealEdwin on 2005-06-22
Try ```
sudo apt-get install at-spi
``` in the terminal.

---

### Post by department27 on 2005-06-22
Not sure how installing at-spi will fix the problem. The mouse can move around the screen but that is about it. Clicking the mouse does nothing.

At a guess it could be something with xorg, and gdm, but could be totally wrong

---

### Post by department27 on 2005-06-22
Some more information. Around the time I started to get the problem I installed the following:

Latest 2.6.10.. 686 kernel
ATI fglrx driver
beagle

---

### Post by Dave_is_sexy on 2005-06-22
Well you should still be able to boot an older kernal from the grub start up menu. Some of those extra listings of ubuntu that appear there are kernel versions to boot (at least they were on mandrake - i'm sure it'll be fine)

chancs are of course it's the graphics card driver upgrade if it was an immedate response. 

Personally I'd just sudo apt-get install gnome and hope it fixes itself? That kinda thing works on windows  ;-)

---

### Post by sapo on 2005-06-22
it happens often in my ubuntu too... and it could look stupid... but is esd that is crashing, and when it crashes the gnome-panel crashes to..

try
killall esd

but its just a 0,01% that it is the problem  ](*,)

---

### Post by TheRealEdwin on 2005-06-22
[QUOTE=department27]Not sure how installing at-spi will fix the problem. The mouse can move around the screen but that is about it. Clicking the mouse does nothing.

At a guess it could be something with xorg, and gdm, but could be totally wrong[/QUOTE]
 The latest updates did what he describes to me and that fixed it.

---

### Post by department27 on 2005-06-23
Hmmm

What i'll try first is install the at-spi. Because the crashes are random-ish, once every 7 days roughly I will see what happens. 

If it still hangs I will go back to the original graphics driver, and wait.

I do have KDE also installed, wonder if it happens in that. Maybe I will try running kde for a while. If it does not happen in KDE then it would rule out the graphics driver, and kernel, and beagle.

I will let you know what I find.

---

### Post by nocturn on 2005-06-23
Hmmm, I heard about that problem on this forum before.
It happens to both ATI and NVIDIA cards.

You specficly need to turn off accellerated rendering.

---

### Post by department27 on 2005-06-23
Could you tell me how I do that. 
Thanks in advance

---

### Post by Remix_88 on 2005-07-15
I have two Dell D600, one is older than the other. 


The older D600 is 1024x768 LCD with IntelPRO Wireless LAN 2100.
The newer D600 is 1440x1050 LCD with Dell WLAN 1350.

Both have an ATI Technologies Inc Radeon R250 Lf [Radeon Mobility 9000 M9] (rev 01) with the acclerated fglrx driver running Hoary with the 2.6.10 i686 kernel and Gnome desktop. Both have 512MB RAM and the same BIOS version. But the hard disks are different capacities.

The newer D600 has always been reliable and never crashed. I have Beagle installed on this machine.

The older D600 has always exhibited the problem you describe where the hard disk light stays fully illuminated, the mouse can be moved, background processes appear to be running but the interface doesn't respond. The problem has been evident on all 386 and 686 kernel versions in the Hoary repositories.

So, we rule out Beagle. That definitely isn't to blame. As for the fglrx driver, I doubt it is to blame either since it doesn't cause me problems on my other D600. But I will disbale acceleration on my problem D600 and see if it helps and report back.

To disable acceleration add the following option to the "Device" section of /etc/X11/xorg.conf

Option "NoAccel" "1"

I am not going to entertain the notion that installing 'at-spi' will fix the problem.

---

