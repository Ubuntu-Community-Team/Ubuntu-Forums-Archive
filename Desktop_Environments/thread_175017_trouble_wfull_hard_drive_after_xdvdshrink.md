---
title: "trouble w/full hard drive after xdvdshrink"
date: 2006-05-12
forum: Desktop Environments
---

### Post by joeybunda on 2006-05-12
Well,

I am somewhat of a newbie, somewhat of a novice.

I am running ubuntu 5.10 and xdvdshrink on my triple boot PC... Win XP, SUSE 10 and Ubuntu 5.10

Here is the trouble - when I installed Ubuntu I only partitioned 5 GB of space. I later installed xdvdshrink - like this: [http://doc.gwos.org/index.php/Xdvdshrink](http://doc.gwos.org/index.php/Xdvdshrink) and I set the working directory here: /home/joe/temp

So 1/2 way through ripping a dvd - I notice that my dvd drive is no longer spinning and that's when I realized that my partition was at 100% full. 

So... closed out xdvdshrink and deleted the temp directory but - my ubuntu partition shows that it is still full - even after emptying the trash can...

I can't figure out how to fix this - the temp directory is gone but the properties of my ubuntu partion still show as full. I tried uninstalling and reinstalling xdvdshrink (after deleting some files) - but still no luck... I cannot seem to find the files (or what is accounting for them) that were ripped. (I am thinking that the files where never ripped - but instead the space was somehow "marked as used")...

Help?

---

### Post by deathbyswiftwind on 2006-05-12
as far as dvdshrink ive never used it but go into nautilus and then view and show hidden folders in your home dir. look for ./xdvdshrink or something along the lines and make sure that there arent any files from the dvd being stored in there 

Best of luck

---

### Post by joeybunda on 2006-05-12
There are no files left out there...

Is there anything like Kdiscfree - that lets you see what files are where. Kdiscfree only lets you see high level partitions - is there an application available that will let someone see the sizes of directories? 

Like "Aceutilities" for windows?

---

### Post by joeybunda on 2006-05-16
Well, Anyone have any ideas?

It's not so much an xdvdshrink problem - my partition is somehow marked and showing it is full - but it is not...

---

### Post by Ramses de Norre on 2006-05-16
If you sure it's displayed wrong: ```
sudo shutdown -hF now
``` to reboot and force an fsck.

---

### Post by joeybunda on 2006-05-16
Forced the fsck - no change...

---

### Post by joeybunda on 2006-05-16
Enabled root, logged in as root, emptied trash....

Problem fixed... However, How the heck did my deleted items end up in root's trash can and why didn't they go away to begin with ???!!!!

---

### Post by changlinn on 2006-05-16
you weren't running xdvdshrink as root or sudo?
You can use df to check your partitions usage.
But "du" is going to be the tool for this if it happens again, just "du -h --max-depth=1" then cd into the bigger folders and find out where that space has been taken up, you would have seen .trash in roots home taking up the space.

---

### Post by changlinn on 2006-05-16
duplicate post, can't work out how to delete

---

