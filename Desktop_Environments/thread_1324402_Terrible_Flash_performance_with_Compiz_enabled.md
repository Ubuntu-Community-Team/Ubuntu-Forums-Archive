---
title: "Terrible Flash performance with Compiz enabled"
date: 2009-11-12
forum: Desktop Environments
---

### Post by thedogisdead on 2009-11-12
Hi everyone, hope you can help.  I've found a few similar complaints to this but wasn't directed to a definitive answer!

With any kind of desktop effects on, Flash (think BBC iPlayer, etc) is almost totally useless - skipping, stuttering video showing only the odd frame and high CPU usage.

I've already had to use the following workaround to keep desktop effects working... without it, the desktop is just black and no effects with work:

[B]In terminal, run these two commands:

Code:

grep XAA /var/log/Xorg.0.log
grep EXA /var/log/Xorg.0.log

One of them will return nothing; the other will return something like this:

Code:

(**) RADEON(0): Option "AccelMethod" "XAA"
(**) RADEON(0): Using XAA acceleration architecture
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)

This tells you which method is currently in use on your system. Whichever one it is, try the other. For me it was EXA, and switching to XAA solved the problem. Here is what to do.

If it reported XAA:

In terminal, do this:

Code:

sudo gedit /etc/X11/xorg.conf

This will give you a text editor window. Paste this into the text editor:

Code:

Section "Device"
 Identifier "my-radeon"
 Driver "ati"
 Option "AccelMethod" "EXA"
EndSection

Save, and reboot, and see if the problem is solved.

If it reported EXA:

In terminal, do this:

Code:

sudo gedit /etc/X11/xorg.conf

This will give you a text editor window. Paste this into the text editor:

Code:

Section "Device"
 Identifier "my-radeon"
 Driver "ati"
 Option "AGPSize" "128"
EndSection

Then save the file and exit the editor, and reboot.

If the problem still isn't solved when you have rebooted, open the file in text editor again, and change it to look like this:

Code:

Section "Device"
 Identifier "my-radeon"
 Driver "ati"
 Option "AccelMethod" "XAA"
EndSection

Then save the file and exit the editor, and reboot.

Both of these solved the problem for me. The first one (with the AGPSize option) is the preferred choice and will result in better performance.

Post back and let us know if it fixes it for you.
Last edited by dwasifar; 5 Days Ago at 12:37 AM.. Reason: better solution 
[/B]

My machine returned EXA.  I'm just adding this in case this problem sheds any light on my Flash problem!

Any ideas, everyone?

Thanks in advance for your help!

Edit: My specs are

2GB DDR Ram,
AMD AthlonXP 2800
ATI Radeon 9200
500GB IDE HP
Karmic Koala

---

### Post by kio_http on 2009-11-12
Try upgrading your graphic driver.

Don't know much about ATI Drivers

---

### Post by thedogisdead on 2009-11-12
Thanks for the reply... what's the best way of doing that?

---

### Post by thedogisdead on 2009-11-17
Any ideas, anyone? 

Thanks again

---

