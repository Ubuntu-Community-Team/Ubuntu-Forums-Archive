---
title: "Less success with multiple OSes -- help!"
date: 2009-05-05
forum: General Help
---

### Post by GL_NORWAY on 2009-05-05
I tried to run a system with 3x Windows XP + 1x Ubuntu Linux (Jaunty).

The three XP partitions are at the three first primary partitions. On these I'm running a multi boot system using PQBoot by Partition Magic that hides the other partitions that are not in use.

Then I made this last Ext3 partition at the end of the HD and tried to install Jaunty on that one. Actually I used the Jaunty installer itself to make this partition. The install process was successful and Jaunty got installed and worked perfectly.

But GRUB got installed too in the MBR. On the first boot after the install of Jaunty, I got the GRUB MS-DOS-like menu that showed some Ubuntu alternatives and my three XP installations. The first XP choice worked and it loaded the first XP partition. But the next two messed up the system completely. It seemed like it tried to run the second partition and the first one (XP) at the same time, since the computer went more or less mad during the start-up and the first partition got partially destroyed. Either GRUB messed things up or it got too messy having four OSes at one disc including Jaunty and GRUB. Or of course I did a mistake during the install of Jaunty.

When everything was tried, at least everything that I could think of, I tried to uninstall GRUB by "fixing" the MBR using the XP service console on the XP install-DVD. GRUB got successfully uninstalled after the MBR got rewritten. But then Jaunty wouldn't start even when I used the PQBoot manager to start it.

I know; this is a complete mess! Luckilly I have a nice backup system and stored images of all my partitions, so there where no sweat fixing things after this. But I'm asking this last time if this is even possible to do before I invest in a HD hot-swap system and puts Jaunty on a dedicated HD -- and then hot-swap to another disc for my XP installations. That should solve everything, but I'm really interested if my original and first idea is even possible to do.

Thanks in advance for any help!

---

### Post by andrew.46 on 2009-05-05
Hi GL_NORWAY,

Your system sounds a little too complex for me to suggest a fix, and for this my apologies. But can I suggest an option that you have perhaps not considered which is to run *all* of these operating systems on a single partition using VirtualBox? This will avoid many of the grub/mbr/partition traps that appear to have snared you somewhat :-).

I attach a screenshot of my own setup to demonstrate the possibilities. This shows a slackware host with windows xp guest.

All the best,

Andrew

---

### Post by GL_NORWAY on 2009-05-05
Thank you for your suggestion! Though, I've ordered a HD hot-swap system, so I'll use a dedicated HD for Linux from now on. I had to conclude that this got a little bit out of control. :P

---

