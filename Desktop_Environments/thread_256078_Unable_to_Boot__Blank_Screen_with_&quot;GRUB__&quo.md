---
title: "Unable to Boot : Blank Screen with &quot;GRUB _&quot; and blinking cursor"
date: 2006-09-12
forum: Desktop Environments
---

### Post by uhavegotmale on 2006-09-12
Hello all,

I am having trouble booting into Ubuntu. I have a Dual boot setup and I did *NOT* install GRUB into the Master boot record. Everything was working fine for over 2 months now, but today after compiz updates when I had to reboot, I can no longer boot into Ubuntu Linux. All I get is a blank screen with "GRUB _" with the cursor "_" blinking. I can boot into Windows fine with no problems. But when I select "Ubuntu Linux" all I get is a blank screen with "GRUB _ " with the cursor blinking

I am not sure if it was because of compiz updates, but I have had lots of problems with the recent compiz updates, but thanks to this amazing community I was always able to find solutions before I had to post my problem. This time I think no one else has a similar problem. Here is my setup

I have a 100 GB single hard drive on my laptop with 2 partitions for Windows XP. C: Drive and D: Drive. When I wanted to install Ubuntu, I resized the D drive to make space for Linux and I made 3 partitions. One ext3 for / , one for swap and a third one, a FAT32, for sharing files between Ubuntu and Windows.

When the installation asked me if I wanted to install GRUB in the MBR, I said NO and installed the /boot in the /root partition. Then I made the windows drive active (using qt_parted) and booted into windows to see if everything was fine. Then I booted with the Linux Rescue CD and copied the "ubuntu.bin" file to share drive and booted back into windows and moved the "ubuntu.bin" file to C: and edited the boot.ini file in windows to add "Ubuntu Linux" option for dual booting.

I pretty much followed the guide on this webpage.
[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)

I am extremely new to Linux, so I am giving all the information I can think of. Also please forgive me if this problem has been answered before. I did search for almost 2 hours on these forums before posting.

If you need further information before you can solve the problem, please let me know and I will be more than pleased to post it here.

Thanks in advance for your help.

---

### Post by uhavegotmale on 2006-09-12
Anyone?

No one has ever seen this problem? Someone please help!

---

### Post by b@nksy on 2007-09-04
Hi,

I am having the same problems as uhavegotmale above.  Is there a solution?

I used the same guide as above except accidently let Grub install into the MBR.  At this point both XP and Ubuntu boot fine.

As I asumed that with dual boot it is better to us the windows loader I ran the fixmbr command in the windows Recovery Command Console.  This gave me back my boot.ini command and I copied the ubuntu.bin to my c:\ and edited the boot.ini to point to this file.

Now XP boots fine, but everytime I try my Ubuntu option I just get a flashing cursor at the top left of my screen.

Can anyone help?

....trust me to 'play' with a working system!  Thanks for any help

---

