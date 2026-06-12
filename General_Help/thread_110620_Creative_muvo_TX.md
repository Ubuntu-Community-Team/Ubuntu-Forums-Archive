---
title: "Creative muvo TX"
date: 2005-12-31
forum: General Help
---

### Post by tubelius on 2005-12-31
Hey, I have problem with my Creative muvo TX. It uses vfat filesystem.

I deleted some of songs using player and it told that I have over 40MB free space. Then I plugged player into my computer, and linux told I have less than 1MB free. I can't fit even one song into it. I don't get what's eating all the space from that player. Let me paste some info:

tubelius@radiant:/media/MP3-SOITIN$ ls -la
total 68
drwx------  14 tubelius tubelius 16384 1970-01-01 02:00 .
drwxrwx---   7 tubelius media     4096 2005-12-31 14:33 ..
drwx------   2 tubelius tubelius  4096 1980-01-01 00:00 #
drwx------   2 tubelius tubelius  4096 1980-01-01 00:00 A
drwx------   2 tubelius tubelius  4096 2005-11-28 22:01 B
drwx------   2 tubelius tubelius  4096 1980-01-01 00:00 C
drwx------   2 tubelius tubelius  4096 1980-01-01 00:00 D
drwx------   2 tubelius tubelius  4096 2005-11-30 16:49 E
drwx------   2 tubelius tubelius  4096 1980-01-01 00:00 F
drwx------   2 tubelius tubelius  4096 1980-01-01 00:00 G
drwx------   2 tubelius tubelius  4096 2005-12-11 19:17 U
drwx------   2 tubelius tubelius  4096 1980-01-01 00:00 V
drwx------   2 tubelius tubelius  4096 1980-01-01 00:00 W
drwx------   2 tubelius tubelius  4096 1980-01-01 00:00 XYZ

tubelius@radiant:/media/MP3-SOITIN$ du -h
13M     ./U
29M     ./V
16M     ./W
15M     ./XYZ
8,7M    ./#
67M     ./A
52M     ./B
69M     ./C
41M     ./D
43M     ./E
41M     ./F
35M     ./G
424M    .

tubelius@radiant:/media/MP3-SOITIN$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              91G   45G   41G  53% /
tmpfs                 252M   16K  252M   1% /dev/shm
tmpfs                  10M  2,5M  7,6M  25% /dev
/dev/hda              4,0G  4,0G     0 100% /media/cdrom1
/dev/sda1             491M  490M  980K 100% /media/MP3-SOITIN



du says I have 424M files and df says I have 490M used.. =/

edit: I tried "df -h --sync", didn't help..

---

### Post by lrmall01 on 2005-12-31
Did you delete them from Nautilus?

I had a similar problem that was coused by Nautilus creating a .Trash folder on the drive and moving things I deleted into that.  So, even though they didn't show up, they were still there in a hidden folder.

In Nautilus, go to View > Show Hidden Files and enable that option.  Make sure there are no hidden directories on the drive.

---

### Post by arch stanton on 2005-12-31
The problem, I believe, is that the deleted files are moved to .Trash-<username>
you need to delete the files from trash to free up the drive space.


I made up a little script to flush the trash on my muvo.

cd /media/usbdisk
rm -r .Trash-arch

hope this helps!

---

### Post by arch stanton on 2005-12-31
hehe photo finish!!

---

### Post by tubelius on 2005-12-31
Thank you for your posts, but it didn't help.

I used player to delete those songs and it told I got over 40MB free space. I checked every directory, no hidden files, no .trash* -files.

Any other ideas? What should I try? :confused:

- - -

I just booted to Win XP pro and checked free space of that muvo, it showed 56 MB. So it works in win xp. Then I booted back to linux and now linux shows 56 MB too. :o

---

