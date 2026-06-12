---
title: "New install 9.04 to 9.10 will not boot!"
date: 2010-04-22
forum: Desktop Environments
---

### Post by Raymond Day on 2010-04-22
I want to test a wireless card. I have a Intel Mini-ITX 2 core Atom 166GHz modle D510MO 64-bit with 4GB RAM.

I installed it with a USB thub drive. Then did a long upgrade from 9.04 to 9.10 desktop.

I installed the Ubutu 9.04 desktop 64-bit then upgraded so I guess it's still 64-bit on 9.10 desktop.

It was working good with my wireless. The firefox icon was black so I rebooted and it shows the GRUB text and blans the LCD screen and just stays there and the LCD power light stays on.

I can press ESC on boot to go to the boot menu. I tested all the lines. It does about the same. On the 2nd boot text goes by and ends and the text stay there. The 1st boot the text blanks.

I installed it on a WD green 160GB SATA hard drive.

Here is a photo of the recovery screen from the 2nd grub line. I think this will help say what's wrong.

[IMG]http://i93.photobucket.com/albums/l41/RaymondDay/Ubuntu/Ubuntuwillnotboot.jpg[/IMG]

I hope some one can help. It was working very good before the 1ST reboot. I can load from the USB thub drive 9.04 I install it with. So from that I guess I could edit somthing so it will boot if any one knows how?

-Raymond Day

I just uploaded a video to you tube to show this:

[http://www.youtube.com/watch?v=EebmxJMfddA]("http://www.youtube.com/watch?v=EebmxJMfddA")

I think I my have to download the 9.10 and install it like that and not do the upgrade to it.

-Raymond Day

I downloaded the Ubuntu 9.10 64-bit and put it on my USB stick. It shows a boot menu to install on the hard drive or run frum the USB stick. But on both them it blanks out the screen and just stays there!

So something is wrong with 9.10 it looks like! 9.04 did not do this.

I guess they have to fix it.

My BIOS on this Intel Mini-ITX D510MO is up to date. I read other place on here and they said that fixed it. But some said it did not too.

I guess I have to use 9.04 or wait till them come out with on over 9.10.

-Raymond Day

---

### Post by mister_p_1998 on 2010-04-23
I had this on upgrading 8.04 to 10.04, you need to get into the grub (using a live cd) its in /boot/grub/menu.lst

find the kernel entry that says:
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=d4324981-8193-4aa1-a5c6-44c4e0aa913e ro quiet splash 

and remove the quiet splash , leaving this:
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=d4324981-8193-4aa1-a5c6-44c4e0aa913e ro

save it and reboot, worked for me..
Steve

---

### Post by Raymond Day on 2010-04-23
Thank you mister_p_1998.

I booted off the live USB stick that has 9.04 on it. It works.

It would not mount the drive. I went in the terminal and typed:

sudo fsck -f /dec/sda1

Press Enter a lot to say yes then it could mount it.

I went to /boot/grub/menu.lst to edit it but it said I don't have permishions.

In the terminal I did sudo apt-get update then sudo apt-get emacs then sudo emacs /boot/grub/menu.lst and I took out the quiet splash from 3 lines near the end and saved it. Did a cat on it to make sure it worked and it did.

Turned it off and with the USB stick out of it went to boot. At lest now the text comes up like it's booting but then it still does the screen black and stays there. So that did not work.

I hope some one else knows a fix.

-Raymond Day

This is not a fix but I just installed 9.04 again and am not going to upgrade it to 9.10. 9.04 works and boots.

But if any one finds a fix for 9.10 please post it here.

-Raymond Day

---

### Post by mister_p_1998 on 2010-04-24
sorry, you needed to type sudo gedit /boot/grub/menu.lst (or whatever text editor you prefer, I like gedit)

---

### Post by Raymond Day on 2010-04-24
I know about sudo. But I don't know how you do root stuff in the desktop.

-Raymond Day

---

