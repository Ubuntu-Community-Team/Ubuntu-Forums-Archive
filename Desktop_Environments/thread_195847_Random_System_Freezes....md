---
title: "Random System Freezes...?"
date: 2006-06-13
forum: Desktop Environments
---

### Post by mbmccormick on 2006-06-13
I'm having a problem with Ubuntu Dapper Drake. Whenever I am working on something or browsing the internet, etc. my system locks up. I can't move the mouse, or click, or type anything. These can last from 5 seconds to 2 minutes. The happen anywhere from every half hour to every few hours. What is causing this problem? Is it graphics related or memory related? Here are my specs:

Ubuntu 6.06 LTS Gnome - Only OS
160GB Hard Disk
256MB RAM
Intel Pentium III 533MHZ
nVidia eVGA MX 4000 Graphics Card

Thanks for any help.

---

### Post by randell6564 on 2006-06-13
Your box is kind of old.  I wanted to test 'ubuntu' in one of my old test boxes (P3 800MHz 512 Ram) and ran into the same thing.)

I'm not by ANY means a computer 'Guru', so it really could be several things!

Once upon a time, before I learned how to partition My HD, I would leave out all the partitions that 'Linux' likes to use (like 'Swap') and would have similar problems!

Post your 'fdisk -l' for everyone to get a looksy!

---

### Post by mbmccormick on 2006-06-15
Here is the data from "fdisk -l"...

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19364   155541298+  83  Linux
/dev/hda2           19365       19457      747022+   5  Extended
/dev/hda5           19365       19457      746991   82  Linux swap / Solaris

Swap is up and running, so no problems there...

---

### Post by randell6564 on 2006-06-15
[QUOTE=mbmccormick]Here is the data from "fdisk -l"...

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19364   155541298+  83  Linux
/dev/hda2           19365       19457      747022+   5  Extended
/dev/hda5           19365       19457      746991   82  Linux swap / Solaris

Swap is up and running, so no problems there...[/QUOTE]

Well...

I'ts been a couple of days.   Are you still experiencing the same problem?

My guess is that Your Processor is just not beefy enough to handle an OS of this type.

I just say that from my own experience!  Remember, I have 800Mhz in my old box. 

Ubuntu 'Dapper' Works Wonderfully in this box! (the one that I use regularly.  1.6GB P4)

So dont let that get you discouraged!  Linux ROCKS!

There are Hundreds of Distros' out there, and many are much smaller than ubuntu.

I would suggest that you go searching for one that is more agreeable to your box.

You can get many as 'Live-Cd's' that will allow you to test them out before installing (Though running from CD will be a little slower than it would be installed on your HD.)

'Puppy Linux' is one that comes to mind.   [http://www.distrowatch.com](http://www.distrowatch.com)   has tons of links to Distros for testing.

Good Luck!

---

### Post by Amon_Re on 2006-06-15
The machine is plentyfull for Ubuntu, that's not the problem.
The newer kernels are rather picky about hardware support tho,  the first thing i'd look into is any output from the kernel while booting, if needed, disable splash.

I'd also check for a bios upgrade, while it's not always a solution, most of my hardware woes have been BIOS/Kernel combinations that borked up.

---

### Post by _mrv on 2006-06-16
Hi,

This also happens on my machine that is not old and has enough RAM (1024MB).

About a week ago I installed Ubuntu Dapper (6.06) in my machine (was using Gentoo before with zero problems...) and now the system freezes several times a day; keyboard and mouse won't work anymore. I don't know about the remote access via SSH because I don't have another machine from which I could try it.

I performed a search in these forums and see that quite many people have had the same problem, but there's no solution nor root cause yet.

_mrv

---

### Post by _mrv on 2006-06-16
BTW, is it possible to see package install history somewhere? I think I didn't have this problem when I installed Ubuntu; it became visible 3-4 days later. Maybe some package update (kernel?) have broken something?

_mrv

---

### Post by _mrv on 2006-06-16
My problem was probably caused by a new RAM; I installed it couple of days ago and ran pretty extensive tests for it and everything seemed to be just fine; that why I assumed that the root cause was not the new RAM module. The new RAM is from the different vendor than the old RAM and there was probably some compatibility issue. Increasing the RAM voltage by 0.1 volts solved the probably. At least for now...

_mrv

---

