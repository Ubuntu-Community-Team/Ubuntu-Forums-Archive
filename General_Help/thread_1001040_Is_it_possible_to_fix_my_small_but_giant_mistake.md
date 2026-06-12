---
title: "Is it possible to fix my small but giant mistake?"
date: 2008-12-03
forum: General Help
---

### Post by cptnff on 2008-12-03
Okay, so heres what happened. Today I did a system back up, but for some reason my home folder was involved in the backup process, that might not seem like a problem, but when you have 60GB worth of stuff in your home folder, you really don't want to back that up. So any way after it was all said and done I went to the folder that stores my backups through nautilus and deleted the backup, but I forgot to shift+delete the backup, so the folder containing the backup is gone, but the space it's taking up  still exist](*,). I checked my .Trash and it wasn't there, and for some reason I can't check my regular trash while in nautilus, (this seem to be an 8.10 thing because I never had that problem in any other ubuntu distro.) but its not in my regular trash either because I can check it while I'm not in nautilus and sure enough no luck there either.

so my question is what can I do other than delete my ubuntu partition and start from scratch? It's taken almost 2 years for me to get ubuntu setup to the point where I'm almost completely happy with it, and starting from scratch REALLY doesn't appeal to me. If you can help me solve this issue, your a guaranteed shoe in for the coolest person alive award:guitar:

---

### Post by Titan8990 on 2008-12-03
If you used sudo to delete it might be in root's trash under /root/

---

### Post by SPr on 2008-12-03
sudo find / -name name_of_backup

will search the hard drive (root + home) for the backup.

If I had 60GB of data in my home directory I'd want it backed up rather than lose it all by accidentally deleting it ;)

---

### Post by cptnff on 2008-12-03
that was the first place I checked. I thought it would be there too, but no such luck.

---

### Post by cptnff on 2008-12-03
> **SPr said:**
> sudo find -name name_of_backup

will search the hard drive (root + home) for the backup.

If I had 60GB of data in my home directory I'd want it backed up rather than lose it all by accidentally deleting it ;)

Its just movies, tv shows, comic books, ect. nothing I'm too attached to, and I don't have enough space to maintain such a back up.

I don't have any other backups and haven't for some time, so don't remember what the name of the back up is. I know that it involves dates and the root user name, but I don't remember how the folder is named. if you could tell me the name of yours, I could just replace it with my user name and todays date and that should do the trick shouldn't it?

---

### Post by ajgreeny on 2008-12-03
**Disk Usage Analyser** may help.  It's in Programs->Accessories and may give you a clue because it should show such a large amount quite easily in the graphical display of files.

---

### Post by SPr on 2008-12-03
> **cptnff said:**
> if you could tell me the name of yours, I could just replace it with my user name and todays date and that should do the trick shouldn't it?

No, I doubt we use the same program, I use Partimage and my own naming convention.

---

### Post by sedawk on 2008-12-03
1) Like said above try sudo find . -name <bigfile> -print
   to find out where <bigfile> has gone.

   Or something like sudo find . -name \*.avi -print 
   to find all video files

2) Check with "du -sk * .??*" to see where the big directories are.
   Start at / and then go "downstairs".

3) Install kdirstat. It shows disk usage with nicely coloured
   "cushions". So you can easily find big files, video files,
   music files, whatsoever. I use it a lot on linux
   and windows (windirstat).

---

### Post by cptnff on 2008-12-03
that was an excellent suggestion, I don't know why I didn't try it before, however no luck there either. Its like the folder went to the osama bin laden school of hide and seek. I don't have a clue where to look. I would try SPr's suggestion but I don't remember the name of the folder. I Would greatly appreciate it if someone would look at their backup folder and tell me how the folder is named. I think its username_12-03-2008_backup or something like that I'm not quite sure.

---

### Post by cptnff on 2008-12-03
> **sedawk said:**
> 1) Like said above try sudo find . -name <bigfile> -print
   to find out where <bigfile> has gone.

   Or something like sudo find . -name \*.avi -print 
   to find all video files

2) Check with "du -sk * .??*" to see where the big directories are.
   Start at / and then go "downstairs".

3) Install kdirstat. It shows disk usage with nicely coloured
   "cushions". So you can easily find big files, video files,
   music files, whatsoever. I use it a lot on linux
   and windows (windirstat).

I have to go pick up my sister from work, but when I get back, I'll try kdirstat

---

### Post by cptnff on 2008-12-03
well I tried kdirstat and I'm sad to say it turned up the exact same results as disk usage analyzer. Does anybody else use simple backup config to do their backups? if so could you navigate to var/backup and tell me whats the name of the folder located inside, because it seems that I'm s.o.l. & j.w.f. without it.

---

### Post by anjilslaire on 2008-12-03
check in
**/home/*username*/.local/share/Trash/**
 and use root access to delete anything that may be there.

---

### Post by EvilRobotDrew on 2008-12-03
i don't know if this will work or not, but you could try booting into a LiveCD, mounting your HD, then unmounting it, the idea being that upon unmounting Ubuntu will say "there are files in the Trash, delete them?" I know with Thumb Drives, if yo delete a large folder, you have to unmount the drive before you can see the free space.

---

### Post by cptnff on 2008-12-03
well I've tried almost all of the suggestions I'll go out and buy some cd's tomorrow and burn a copy of ubuntu so I can try EvilRobotDrew's suggestion. I wish I had one right now but the last live cd I had was edgy and I gave that to a friend a long time ago.

---

### Post by anjilslaire on 2008-12-03
If you have a usb drive, you could install the live cd to a flash drive & run it from there too

---

### Post by Slim Odds on 2008-12-03
You do know that *small* and *giant* are **antonyms,** right?

---

### Post by cptnff on 2008-12-03
I couldn't wait until tomorrow so I asked a friend of mine for a blank disk. Once again nothing. My next plan is to wait until midnight to do another backup so I can find out how the folder is named that way there won't be 2 from todays date. Hopefully this will solve the issue.

---

### Post by sambarusty on 2008-12-03
this may be a stupid question, but what if you just do a df -k at root and find the largest directory, then work recursively, it has to be somewhere correct. I mean it needs to be somewhere removable. You could even write a short script if you wanted.  Good luck.

---

### Post by sambarusty on 2008-12-03
sorry when I say recursively I mean selecting a drive so df -k /something

---

### Post by cptnff on 2008-12-04
It's official, I have now tried every suggestion on this thread, and have yet to find the folder. I don't know how or why but for some reason the folder seems to be nonexistent. I'm tired and I'm going to bed. I'll be back tomorrow to see if any of the brilliant minds that make up the ubuntu community have come up with an answer. Thanks to everybody who stopped by here today to give me some assistance, even if it didn't solve things I still appreciate the fact you took time out of your day to help me out.

---

