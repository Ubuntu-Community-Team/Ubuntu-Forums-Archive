---
title: "Cannot increase resolution on Intel 82915G"
date: 2010-03-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Anton90125 on 2010-03-09
Hello,

This is my second thread concering my problems with getting the monitor resolution to change/increase. 

The tread being : "Unable to change monitor resolution".

The main detals are:

 I am a newbie to Linux and thought I would get Ubuntu to learn about this  OS. I got a second hand PC from Ebay a DELL GX280 P4 2.8GHZ. I set this  up as a duel boot and successfully installed Ubunto 9.10.

Everything seems to be ok except the monitor (IIyama HM903DTA Vision  Master Pro 454) resolution seems to be restricted to 800 x 600 (60 Hz)  and 640 x 480 (60 Hz). I know that the monitor can go higher as I use it  with windows 1024 x 768 (85 Hz).

When i try System>Preference>display I get unknown monitor.

I have these bits of infomation:

 00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL   Integrated Graphics Controller (rev 04)

From various tests done (from advice from "RealZippy") it seems that ubuntu is not able to use the resolution features in the Intel chip set. Any help would be greatly appricated.

Cheers

Anton

---

### Post by Slipstick-Joe on 2010-03-19
My solution, which worked on a different Dell, with different Intel Integrated Graphics, was to boot with the "nomodeset" option.  To do this once, as a test, you can add this option as you boot:

You probably don't see a "Grub" menu during boot.  (The boot menu is hidden by default if you have only one OS installed.)  Hold down the "Shift" key during boot in order to see the boot menu.  (Don't bother if you always see the "Grub" menu.)

When the "Grub" menu is displayed, hit the "e" key.  This will call up a simple editor.  Use the cursor keys to navigate to the line that ends with "quiet splash".  Add the word "nomodeset" to the end:

(original)...........quiet splash
(edited).............quiet splash nomodeset

Then hit CTRL-X, which will resume your boot, but with the one-time edit in place.

If you're lucky, you will be able to log in and select from a wider range of display resolutions.  In that case, you'll want to make that edit permanent.

To do so, open a terminal window with "Applications" | "Accessories" | "Terminal".  Type:

[FONT=Courier New]gksu gedit /etc/default/grub[/FONT]

Enter your password when requested.  Change the line

[SIZE=2]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/SIZE]

[FONT=Verdana]to[/FONT]

[SIZE=2]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"[/SIZE]
[FONT=Verdana]
Save the file, and exit the editor.  Back in the terminal window, type:[/FONT]

[FONT=Courier New]sudo update-grub[/FONT]

and enter your password when requested.  That should do it.

Good Luck.

---

