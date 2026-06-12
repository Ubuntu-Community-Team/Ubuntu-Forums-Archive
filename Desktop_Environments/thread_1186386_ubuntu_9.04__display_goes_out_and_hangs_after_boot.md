---
title: "ubuntu 9.04  display goes out and hangs after boot"
date: 2009-06-13
forum: Desktop Environments
---

### Post by perks.williams on 2009-06-13
Hi All,
I did a fresh installation of ubuntu 9.04 on my PC

AMD x2 dual core processor
1.5 GB Ram DDR2
Nvidia 6150 Geforce onboard card.
Asus M2N-MX mother board.
Segate Sata HD
Samsung Sync Master 740N monitor

once installation was completed, I restarted and booted into ubuntu and everything went fine. But after 2 minutes the display started flickering with a mix of colors (image of monitor is attached) and none of the keys worked. Looks like its hanged.

I restarted it again and found the same thing happening. Next time I restarted I tried pinging my PC from a laptop connected to the same router and it pinged. But once this happens it stops pinging, that means the system gets hanged.

I tried logging into recovery mode and got into shell with network and managed to install Nvidia driver 180 using the below commands

       sudo aptitude install envyng-core
       envyng -t

And the graphics was fine in next boot but still after 2-3 minutes the same thing happened my display went crazy showing diff colors.

I tried changing the refresh rates in nvidia settings, but same thing.

Please help me to solve this problem.

---

### Post by pastalavista on 2009-06-13
Next time you boot into the desktop, go right away to System->Administration->Hardware Drivers. Disable whatever is seleced and if a different choice is avalable try it. If none are available, go to System->Preferences->Appearance, click the 'effects' tab and select 'none'.

If none of this helps, try Recovery Mode again and select 'Fix broken Packages' and 'Repair X' and reboot.

edit: as to hardware drivers, I was only referring to graphics drivers. don't disable wi-fi or other peripheral drivers

---

### Post by brett- on 2009-06-13
I had the exact same trouble with 9.04 running on AMD64 dual core with ATI chipset and onboard video.  I removed fglrx and went with the default display package.  All is well now.

---

### Post by perks.williams on 2009-06-14
Thanks guys for your reply, but nothing worked.

I tried removing nvidia driver 180 and activated 173, but same  thing.

pastalavista can you make your point more clear.If i get it right, I think you are telling to go with default driver. Actually soon after the installation at the first boot before even installing nvidia driver I had the same problem.

Changing effects to none also dint help.

Tried even doing repair X from recovery mode, but dint help.

I am feeling really unlucky with this... Please someone help me out.

-A William

---

### Post by perks.williams on 2009-06-14
More updates.... I am getting the same issue after booting from and USB also....

I tried even 8.10 and its the same thing happening with that too...

Recovery mode without graphics works fine. So this is something fishy with graphics. But then how come windows XP is working fine in this system.


-A William.

---

### Post by perks.williams on 2009-06-14
Ok some how I was able to dig out the problem....

The M2N-MX board was not compatible for Linux.... I tried Fedora and RHEL , the result was same.

Now I disabled apic in BIOS and ubuntu 9.04 works with a charm....

-A William.

---

