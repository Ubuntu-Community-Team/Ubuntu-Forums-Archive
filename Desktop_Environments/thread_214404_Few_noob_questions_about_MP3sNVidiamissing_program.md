---
title: "Few noob questions about MP3s/NVidia/missing programs/browser fonts/newsreader"
date: 2006-07-12
forum: Desktop Environments
---

### Post by gene0915 on 2006-07-12
I installed Kubuntu about a month ago. My system was configured perfectly and all was well. I installed the latest Nvidia drivers for my GeForce 6600 and started having some issues so decided to look for another distro. After playing with Mepis, Linspire, FC5, Xandros, Mandriva, FreeBSD, Knoppix, PCLinux, Suse and Gentoo...... I'm back to Kubuntu 6.06. :) Here are a few problems I can't seem to fix:

1) With the base install of Kubuntu 6.06, my GeForce 6600 and Princeton Ultra 72 monitor work together in 1024x768@75 refresh rate and it's fine. (Perfect setting for my eyes.... it's what I run my Windows XP install at.

When I install the latest NVidia drivers, I only have the option of picking a refresh rate of 70 max which makes my monitor put off an ear shattering, high pitch scream from time to time especially on white screens. Is there some program that I can download that lets me FORCE changes to some X server setting and give me back the option of picking 75k?

2) I have my NTFS SATA drives mounted perfectly in FSTAB and can access them just fine. When I browse to my MP3 collection on one of my Windows drives and double click on a song, it loads into XMMS and just sits there. If I go into XMMS and click on FILE/OPEN/etc and browse out to the file that way, it will play from the Windows drive. If I copy the file to my Kubuntu home directory and double click on the file, it will play perfectly. When I had Kubuntu installed a month ago, I did NOT have this problem. I could use the file manager and browse out to my Windows mounts and double click on an MP3 and XMMS would load and start playing. Now it won't..... any ideas?

3) Numerous times I used Synaptic to fetch a program. It downloads and installs the program but some times it will not show up when I click the "start" button and poke around. I can often fix this by logging out and back in and then it will appear in the menu. A few times I've had to manually add it to the menu. Why don't programs that download with Synaptic always appear in the "start" button menu?

4) Using the default web browser in Kubuntu 6.06, I've noticed the fonts are small. To small for my liking. I know how to go into the browser settings and increase the size of the fonts but these changes won't "stick". If I close the browser and open it back up, it's back to the small font size. How can I increase the font size and make it permanent?

5) On the PC, I have a binary leecher program named Grabit. What I love about it is I can tell it to start 4 concurrent connections to my WOWWAY account and start downloading something then tell it to connect to my Astraweb account and pull down another 4 threads from them for the same file. Is there a GUI/user friendly equal to this program in Linux?

System specs in case they're needed:
ASUS P4C800-E Deluxe m/b
P4 3.0GHz HT
GeForce 6600 AGP 8X
SB Audigy 2 Value edition
1 gig of DDR ram
Princeton Ultra 72 monitor
C: SATA 160 gig NTFS
D: SATA 320 gig NTFS
E: 100 gig IDE Linux (Kubuntu)
F: NEC 3520A DVD+RW burner

Thanks!

---

### Post by gene0915 on 2006-07-13
24 hour bump

---

### Post by gene0915 on 2006-07-15
48 hour bump

---

### Post by tzulberti on 2006-07-16
> **gene0915 said:**
> I installed Kubuntu about a month ago. My system was configured perfectly and all was well. I installed the latest Nvidia drivers for my GeForce 6600 and started having some issues so decided to look for another distro. After playing with Mepis, Linspire, FC5, Xandros, Mandriva, FreeBSD, Knoppix, PCLinux, Suse and Gentoo...... I'm back to Kubuntu 6.06. :) Here are a few problems I can't seem to fix:

1) With the base install of Kubuntu 6.06, my GeForce 6600 and Princeton Ultra 72 monitor work together in 1024x768@75 refresh rate and it's fine. (Perfect setting for my eyes.... it's what I run my Windows XP install at.

When I install the latest NVidia drivers, I only have the option of picking a refresh rate of 70 max which makes my monitor put off an ear shattering, high pitch scream from time to time especially on white screens. Is there some program that I can download that lets me FORCE changes to some X server setting and give me back the option of picking 75k?

You can configure xorg "directly". To do this, in a console write: "sudo dpkg-reconfigure xserver-xorg". It will ask you about a few things. Press Enter until it ask you about the resolution. There choose advanced.


> **gene0915 said:**
> 
3) Numerous times I used Synaptic to fetch a program. It downloads and installs the program but some times it will not show up when I click the "start" button and poke around. I can often fix this by logging out and back in and then it will appear in the menu. A few times I've had to manually add it to the menu. Why don't programs that download with Synaptic always appear in the "start" button menu?

You should download a package name menu, and if a program does not appears, write form a konsole update-menus (i cant remeber if it was update-menu)

I can not answer the other question becuase i do not know was it happening

---

### Post by stoffepojken on 2006-07-16
1) Try to set the resolution to "1024x768_75" in /etc/X11/xorg.conf

---

