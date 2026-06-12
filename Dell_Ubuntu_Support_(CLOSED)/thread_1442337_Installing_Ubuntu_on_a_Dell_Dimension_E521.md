---
title: "Installing Ubuntu on a Dell Dimension E521"
date: 2010-03-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Delluntu on 2010-03-29
I'm wanting to install Ubuntu on my sisters old Dell but am having some difficulties.

I download the Ubuntu ISO, burn it to a CD, and insert it in the computer but cannot run a Live CD.  The last time I played around with Ubuntu a few years ago I was always able to boot from the CD but apparently, not anymore.   Instead I get some error message stating that there is no bootable CD detected, to insert one, and press F1.

So I boot up Windows and am introduced to this thing called Wubi.  Okay...Maybe it's the same.  So I double click the icon to run the CD but get the following error:

"No CD detected, cannot run CD menu"

....Okay..But there is a CD IN the drive...?  I find it rather ironic that my first attempt at installing Linux results in an error.  So I try a workaround.  I right click the icon, click "Explore" and a new window pops up showing the contents of the disc.  I then double click the icon labeled "wubi."

Success!  The "Ubuntu Installer" appears!

I then check out all of the options but I notice that the largest installation size I can choose is 30GB.  That sucks, am I not going to be able to take up the entire hard drive with Ubuntu?  I want to completely rid myself of Windows not coexist with it!  Whatever, I just go ahead and choose 30GB and begin the installation.  After a few minutes it is finished and asks to reboot.  The computer then reboots into Ubuntu and continues installing.

After the installation is complete the system reboots, but loads Windows instead of Ubuntu.  I reboot again and am prompted with:

"Please select the operating system to start:"

I highlight Ubuntu and hit enter.

I then am prompted with the following:

"GNU GRUB version 197~beta4

[ Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists possible device/file completions. }

sh:grub> _"

The HECK does that mean?!  I force the system to reboot but again am prompted with the same message.  I reboot and launch Windows, Uninstall Ubuntu with Wubi, reinstall it, but alas get the same message yet again.  This is frustrating.  I have burned 3 CDs and they all have the same error.  Any ideas?

---

### Post by franklamoureux on 2010-06-20
I got my upgraded E521 running 10.04 wit *almost* no problems.

1. Make sure you have the 1.1.11 BIOS
2. Make sure your BIOS is set to boot on CD drives first
3. Follow the prompts

Mine installed like a charm. Here is my current config:
- BIOS : Dell 1.1.11
- AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ (125w - [[COLOR="Blue"]_details_[/COLOR]]("http://products.amd.com/en-ca/DesktopCPUDetail.aspx?id=34"). I upgraded it from a 3800+)
- 4x1GB DDR2 533MHz
- nVidia GeForce 7300 LE
- Western Digital WDC WD1001FALS-0 (1TB)
- Western Digital WDC WD3200KS-75P (320GB)
- D-Link DGE-530T Gigabit Ethernet Adapter
- Ubuntu 10.04


By default the E521 came with only one HD and if you look around you'll find that putting 2 HD is not good for HD temps. I wanted/needed 2 anyway.

Problems I ran into and resolved:
- HD are overheating. 
  Solution: 
    - Use a metal file and buff the right side of the plastic blue sliders holding the drives. Keep some at both end to guide and hold the drive.
    - Drill holes in the bottom of the case and on the right side of the metal tray to allow air vent
    - Add 2 Antec Tri-cool ([[COLOR="#0000ff"]_link_[/COLOR]](http://store.9289.com.au/index.php?main_page=product_info&cPath=77_200&products_id=2843)) fans. One screwed on the back of the case, pushing air out. One taped to the bottom of the case pushing air towards the drives. Run them at Medium speed.
    - Now HD temps are 37C / 40C idle (while they were at 47C / 51C before)
- Can't use AMD heatsink.
  Solution:
    - Reuse Dell's heatsink
    - Use fresh OCZ Freeze Thermal Compound. CPU cores (2) runs at 18C and 38C idle. Goes above 55 when doing CPU intensive stuff (not good...)

Problems still to be resolved:
- Case fan speed. It always runs at the same low speed. Result: Core 1 temp is 18C while Core 2 temp is 38C idle. If I was able to control the case fan speed it would lower the temperature. The problem:

[INDENT]/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed[/INDENT]

From [[COLOR="Blue"]_this thread_[/COLOR]]("http://en.community.dell.com/support-forums/desktop/f/3514/p/18804126/18927112.aspx") it looks like the fan **IS** pwm-capable, but Ubuntu won't detect it... 

I also tried ik8ctl, ik8fan etc, but it says that my BIOS is not compatible (of course it's not a laptop!).

---

