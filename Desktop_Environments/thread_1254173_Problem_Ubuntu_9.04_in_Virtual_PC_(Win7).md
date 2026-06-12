---
title: "Problem Ubuntu 9.04 in Virtual PC (Win7)"
date: 2009-08-31
forum: Desktop Environments
---

### Post by gcanny on 2009-08-31
I have used VPC 2007 to run Ubuntu 8.04 with good results... So, this weekend I install the newest release of VPC for Win7 (used to run XP mode in Win7) and installed Ubuntu 9.04 into a VM.  The install went okay but the VM never detects the mouse...?  First, anyone have an idea how to get the mouse working in the Ubuntu 9.04 VM?  Second, are there keyboard short-cut to operate the GUI from the Keyboard?

---

### Post by davebe2 on 2009-09-19
Having similar problems - seems to be a limitation of Win7 VPC  . . . 

According to MS doco,   Win7 VPC only supports MS OSs . . . .

---

### Post by philcamlin on 2009-09-19
since 7 is beta could it be a bug in windows 7 itself?

---

### Post by davebe2 on 2009-09-21
> **philcamlin said:**
> since 7 is beta could it be a bug in windows 7 itself?

Phil - nice thought, but as I am using RTM-Final, it's now a "permanent" feature  ! !    !:sad:

---

### Post by EvilJ on 2009-09-25
I got this fixed but it took some digging and some serious work...
 
I was able to install into VPC in Win 7 by using the keyboard. Once I got it installed and rebooted, the system started but I had no mouse. Alt+F1 will jump you to the applications menu at the top of the screen. Go there, accessories, terminal. Once you are in the terminal, everything else can be done there.
 
First thing; you need to add an "InputDevice" section into xorg.conf. It never gets created by the installer.
 
*sudo gedit /etc/X11/xorg.conf*
 
Add the following section: (See Claus's response from Jan 6, 2009 at [http://arcanecode.com/2008/11/10/installing-ubuntu-810-under-microsoft-virtual-pc-2007/](http://arcanecode.com/2008/11/10/installing-ubuntu-810-under-microsoft-virtual-pc-2007/))
 
*Section &#8220;InputDevice&#8221;*
*Identifier &#8220;Configured Mouse&#8221;*
*Driver &#8220;mouse&#8221;*
*Option &#8220;CorePointer&#8221;*
*Option &#8220;Device&#8221; &#8220;/dev/input/mice&#8221;*
*Option &#8220;Protocol&#8221; &#8220;ImPS/2&#8243;*
*Option &#8220;ZAxisMapping&#8221; &#8220;4 5&#8243;*
*Option &#8220;Emulate3Buttons&#8221; &#8220;true&#8221;*
*EndSection*
 
As per his instructions, also edit /etc/modprobe.d/options:
 
*sudo gedit /etc/modprobe.d/options*
 
Add this line: (It will probably be the only line in the file)
 
*options psmouse proto=imps*
 
Finally, we must edit the boot options to make it work.
 
*sudo gedit /boot/grub/menu.lst*
 
Find the line in the first boot section that begins with "kernel". Add the following two options to the line between 'ro' and 'quiet':
 
*noreplace-paravirt i8042.noloop*
 
So the final line looks like:
 
*kernel /boot/vmlinuz-2.6.28.11-generic root=UUID=<some guid> ro noreplace-paravirt i8042.noloop quiet splash*
 
When you've made those edits, reboot with a '*sudo reboot now'* and you should be able to capture the mouse by clicking in the Ubuntu window after restart. However, since there are no integration components for the Ubuntu platform, you have to manually release the mouse with 'Ctrl+Alt+Left Arrow'. It doesn't matter which Ctrl and Alt keys you use... both work.
 
Also note in the link above, there is a display section you may want to consider adding. This allows you to change the display size.

---

### Post by davebe2 on 2009-10-01
To EvilJ .  .

**Thanks for your advice .** . .       I now have the mouse problem solved  . . . :smile:    . . . ! 
I also added the extra Display properties, but it's yet to change.  Next steps - go back and see if I inserted the extra coding correctly.
I've also yet to get any Sound - so more investigation needed here  . . .   (Pics and movies OK, but cannot yet link to the Mobo Sound device for any output) . .

However, even though I have given the Ubuntu-VM  756M  (4GB total in the PC),   it runs like a dog - especially when transferring data from the Windows files  (20kb / sec !) . . .     :confused: . . . 
      ** Any thoughts anyone on  this aspect  ? ? **

Cheers, daveb

---

