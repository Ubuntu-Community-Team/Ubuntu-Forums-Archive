---
title: "Boot loader issue"
date: 2005-12-28
forum: General Help
---

### Post by Mike_N on 2005-12-28
Okay, up until yesterday, when i turned on my PC, it asked me if i wanted to boot into Windows, Ubuntu or Ubuntu recovery mode... A friend of mine set this up for me by the way...

Yesterday, when i turned on my machine, it asked if i wanted to boot into one of like five Ubuntu types and none of them could boot succesfully anyway...

So i open it up and unplug the Windows drive, Ubuntu boted up fine... Then i unplugged the Ubuntu drive and Windows booted up fine...

Only thing i really did yesterday was get the auto update from Ubuntu, could that of mesed up my boot loader?

I hope i'm explaing this well enough and that one of you fine folk might have the  answer... Thanks, Mike

---

### Post by rcerreto on 2005-12-28
[QUOTE=Mike_N]Only thing i really did yesterday was get the auto update from Ubuntu, could that of mesed up my boot loader?[/QUOTE]

Yes, looks that way.
Look at 
/boot/grub/menu.lst
toward file end you'll find several entries related to the kernels you can boot.

Just below the lines starting with "title" you should have lines starting with "root".
There follows something like hd(0,0)
The first digit (the hd you're booting the OS from) must be different between Windows entries and linux ones. Since the OSes are on different disks.

If linux entries relates to hd(0,<some-digit-here>) change them to hd(1,<unchanged-digit-here>).
It should work now.

BTW: the update shouldn't cause that mess. Something is wrong in your config files. First guess is in /boot/grub/device.map : there should be two lines in it. Is that true?

---

