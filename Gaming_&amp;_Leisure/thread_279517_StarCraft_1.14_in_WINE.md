---
title: "StarCraft 1.14 in WINE"
date: 2006-10-18
forum: Gaming &amp; Leisure
---

### Post by Consumed on 2006-10-18
So I have successfully installed StarCraft and Brood War and patched to 1.14 but whenever I attempt to run it, I get the missing CD error.  I have already did the auto-detect for the drives.  I have already checked the drives in winecfg and it *does* point correctly to the CD drive.  I made sure the CD drive is also set to be a CD drive.  I saw an older thread that said sometimes a no-CD loader will work so I was able to run BWLauncher from bwprogrammers.com and that crashes when attempting to update to run 1.14.  At this point I think purchasing Cedega is not an option for me either.  Any other ideas I can try?

---

### Post by pay on 2006-10-18
A new cd crack from [www.gameburnworld.com](www.gameburnworld.com) might work.

---

### Post by Consumed on 2006-10-18
They don't even have a no-CD loader for 1.14.

---

### Post by CatKiller on 2006-10-18
FWIW, StarCraft works fine for me without a no-cd crack or anything like that. winecfg's Drives section has my cdrom drive listed as D: /cdrom/ and Type: Autodetect.

Is the cd in the drive that you installed from?

EDIT: Wine 0.9.22, btw. Don't know if that makes a difference, but it's worked with whatever versions were in the budgetdedicated repository since Dapper came out. Hadn't tried it before then.

---

### Post by Consumed on 2006-10-20
Okay, so I have successfully been able to run StarCraft 1.14 with WINE.  After following the HOWTO install StarCraft on Dapper guide and then updating to 1.14 using the patch program from blizzard.com, I ran into the issue of it stating the CD was missing.  I tried changing my mount points, made sure everything was correct and still it gave me this issue.  I read a no-CD crack may remedy the issue.  I downloaded BWLauncher from bwprogrammers.com for 1.14 and it required an update to launch SC, which it downloads and then crashes upon exit and does not update upon relaunching.  To work around this issue, I had a friend on Windows download BWLauncher, do the required update, zip all files in the folder, sent it to me, and was able to run this BWLauncher with no issues.  I selected only the 1.14 no-CD crack and got SC working.  Now I had the issue of BNet crashing StarCraft.  Upon reading a Cedega guide, it mentioned you must install MS fonts using the following terminal command: 
sudo apt-get install msttcorefonts

Once all this was done, I was in good shape and had no issues.  Hope this may help some people out there.

---

### Post by Consumed on 2006-10-20
Well, I take that back... Sounds do not play, but I'll attempting figuring that out a tad later unless anyone feels like posting here.

---

### Post by 043087m135 on 2007-04-21
Hey all. Just wanted to make a little post re: starcraft functionality and the no cd thing. I was able to open starcraft successfully without any nocd crack or the cd in the drive. I mounted the iso to /mnt/starcraftbw and specified that directory as a autodetect type drive in winecfg. worked like a charm for me. good luck!

---

