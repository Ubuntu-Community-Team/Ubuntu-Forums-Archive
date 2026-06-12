---
title: "Wine/crossover office install with multiple cd's"
date: 2005-12-01
forum: Desktop Environments
---

### Post by stevea1210 on 2005-12-01
I am trying to install Garmin Mapsource City Select, and have run into an issue.  It is a three cd install, and when the first cd is done, it says it is looking for the second cd and can't find it.  The drive is still in use and won't allow me to unmount it, so I can't eject the cd and insert the next one.  I have the same issue with the newest wine and newest crossover office.

I have tried a few things that haven't worked:

I copied the cd's to my HD into separate folders inside of the same folder – same error.

After running the install out of the first cd's folder on the HD, I copied the data from the second cd's folder into the folder of the first cd. -- same issue

I created one iso containing all three cds worth of info, mounted that, and tried launching from there. -- same issue

I created a separate iso of each cd, mounted the first iso, ran the first part of the install.
When it asked for the second cd, I mounted the second iso over the first.  --same problem.

I have read about some of the above working for some people.  None of them worked for me.  Does anyone have any other ideas I can try?

---

### Post by discord on 2005-12-02
Maybe you should try to get help from the crossover office team...or on a wine mailing list. Only thing i can think of is maybe you should copy the files from cd all into one directory, either that or make isos of each disk and mount them at three different locations. then refer to each mount point when it asks you for the disk...

---

### Post by stevea1210 on 2005-12-03
Thanks discord.  I think I’ll give the crossover/wine support a shot.  As for your suggestions,  I appreciate them; however, they won’t work in this situation.

> Maybe you should copy the files from cd all into one directory

I didn’t mention this, but the first and second cd’s are both install cd’s with their own setup.exe files, and other files with the same name (not quite a typical install).  

> Make isos of each disk and mount them at three different locations. Then refer to each mount point when it asks you for the disk...

Unfortunately, it won’t give you an option to point it to a new location when it wants the second cd.  It only gives you an option of retry or cancel the install, when it can’t find a cd.

---

### Post by Webnapper on 2007-12-09
Hi Stevea,

I'm running into the same Problem. Did you manage to solve this Problem?

Greetings
Thomas

---

### Post by doug1212 on 2007-12-09
To install from multiple cd's in wine I believe the the command is```
 wine eject
``` in a terminal window.

Doug.

---

### Post by Webnapper on 2007-12-10
Thanks Doug,

this helped alot.

I just have a new problem now. The Garmin installer doesn't recognize the new CD. It seems that WINE is mountig it correctly. 

Thomas

---

### Post by entropathy on 2008-05-21
I was having the exact same issue installing WoW...I finally got it to work by running the normal install and when it asks for the 2nd disc just open a new terminal and umount your cdrom device, then push the button on the cd drive to eject the disc...insert the new one and remount it in the same place you umounted it from...the crossover installer notes the new disc when it gets mounted and installation continued, i didn't have to do anything inside of cxoffice during this install..I also don't have any sort of automounter running...

---

