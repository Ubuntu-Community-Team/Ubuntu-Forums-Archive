---
title: "Ubuntu Jaunty + Windows XP Dualboot"
date: 2009-06-18
forum: General Help
---

### Post by rfkrocktk on 2009-06-18
I'm planning on formatting my hard drive and installing Jaunty this weekend. I had a few questions about dual-booting before I do it, especially since I haven't configured a dual-boot system before. 

My main operating system is and will always be Linux. XP is only going on my computer because I need it for my DAW software + hardware integration. (I use Cakewalk's SONAR Producer line for audio production, and I use a firewire Presonus FirePod for my input source.) 

I have had Windows XP on this computer for a really long time, and it's definitely time to format the drive and get rid of all the crap that Windows left on it :) 

So my first question is this, how should I go about formatting it? Which operating system should I install first? I really like the way that Ubuntu handles formatting drives, and Windows doesn't really offer me an option for formatting itself. 

Does anyone have any tips? What should I do?

---

### Post by Therion on 2009-06-18
Setting up a dual-boot is a piece of cake if you do it the right way.  Installing XP first will make things eaiser in the long run though.  

Follow this tutorial and you're good to go:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by Amilo1718 on 2009-06-18
you shouldn't go for a dual-boot :D
especially audi/midi software in linux is top of the edge...

but if you still want a MS OS try wubi ;)

---

### Post by Muscovy on 2009-06-18
To make things easiest, try reinstalling Windows and completely overwrite (be sure you back up!), then add an Ubuntu partition afterwards. 
  When installing Ubuntu, on the page for hard drive usage, CLICK SIDE BY SIDE, NOT full, and slide the bar around until you have the right sizes of partitions. I'd recommend loading all your Windows stuff first, so you can give yourself a more accurate overhead.
  I think that's it.

---

### Post by merlinus on 2009-06-18
Be sure to delete temp and unneeded files and defrag before resizing windows.  You may also need to disable the paging file, and after resize activate it.

Welcome to the forums, and please use the search feature to see if you can find help in various threads about your issues and questions first.

---

### Post by Hobgoblin on 2009-06-18
> **rfkrocktk said:**
> Windows doesn't really offer me an option for formatting itself. 


If you have a Windows install disk, boot from that, I forget the exact options to select but it is possible to remove the current partitions and then install to part of the drive.  This will save you having to resize the NTFS partition to install Ubuntu.

Once XP is set up then boot from the Ubuntu CD and install that as normal.

---

### Post by hibliss on 2009-06-18
What are the specs on your machine?

You May be able to get away with running XP in Virtual Machine and with Virtual Box guest additions, you will have all of your hardware usable.

---

