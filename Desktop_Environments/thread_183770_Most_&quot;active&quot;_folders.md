---
title: "Most &quot;active&quot; folders"
date: 2006-05-28
forum: Desktop Environments
---

### Post by OtonVM on 2006-05-28
Hello everone!

Oki, here it goes, my fist thread here.

So to the point. I am planing a switch from gentoo to ubuntu on the 1st of june (or maybe the 2nd, depends on the seeds on bittorrent ;)  ). As a former gentoo user you can imagine I am quite preoccupied with performance. I am used to having 14 partitions, each with it's own settings for better acces times and such. My questions are: where does apt store it's downloaded files and extracted files? How big does this folder usualy get? Are all logs still in /var/log? Where are the applications stored? /usr/local or /opt (since they are precompiled). Temp folder? /tmp or /var/tmp (I have both)?
I need this info so I can make them ext3. As an example, how do you like this scheme?
/dev/sda1 --- windows
/dev/sda5 --- windows data
/dev/sda6 --- /boot --- 100MB
/dev/sda7 --- / --- 30GB
/dev/sda8 --- swap --- 512MB
/dev/sda9 --- /home --- 20GB
/dev/sda10 --- /var --- 5GB (since I don't know about logs and temp)
/dev/sda11--- /tmp --- 5GB
/dev/sda12 --- /mnt/download --- 120GB (ext3, to share with windows)
/dev/hdc1 --- /mnt/storage --- 115GB (same as above)

Tnx in advance!

---

### Post by ifokkema on 2006-05-28
[QUOTE=OtonVM]Hello everone!

Oki, here it goes, my fist thread here.

So to the point. I am planing a switch from gentoo to ubuntu on the 1st of june (or maybe the 2nd, depends on the seeds on bittorrent ;)  ). As a former gentoo user you can imagine I am quite preoccupied with performance. I am used to having 14 partitions, each with it's own settings for better acces times and such. My questions are: where does apt store it's downloaded files and extracted files? How big does this folder usualy get? Are all logs still in /var/log? Where are the applications stored? /usr/local or /opt (since they are precompiled). Temp folder? /tmp or /var/tmp (I have both)?
I need this info so I can make them ext3. As an example, how do you like this scheme?
/dev/sda1 --- windows
/dev/sda5 --- windows data
/dev/sda6 --- /boot --- 100MB
/dev/sda7 --- / --- 30GB
/dev/sda8 --- swap --- 512MB
/dev/sda9 --- /home --- 20GB
/dev/sda10 --- /var --- 5GB (since I don't know about logs and temp)
/dev/sda11--- /tmp --- 5GB
/dev/sda12 --- /mnt/download --- 120GB (ext3, to share with windows)
/dev/hdc1 --- /mnt/storage --- 115GB (same as above)

Tnx in advance![/QUOTE]

Hi,

Well, let's see...

- Apt stores downloaded files in /var/cache/apt/archives/.
- Extracted files will be all over the place. Docs in /usr/share/doc/, bin files in /usr/bin/ or the like (/usr/sbin/, /bin, /sbin). Libraries in /lib/.... etc etc etc.
- The cache can get really big if you keep upgrading, but it's easy to clean (there's a command).
- Logs are in /var/log/, yes.
- /usr/local/ is not really used much, mine is only 116 Kb large :) Then again, I usually don't compile stuff exept for my own small programs.
- Temp folder is /tmp/.

Maybe helpful to you, this is the diskusage of my root directories. Please notice that this system hasn't been installed that long. I have left my home partition out, obviously... :)

```
36M     ./etc
68K     ./tmp
15M     ./boot
4.0M    ./bin
1.7G    ./usr
8.0M    ./sbin
147M    ./lib
214M    ./var
268K    ./root
3.0M    ./dev
28K     ./media
900M    ./proc
0       ./sys
```
2.2 Gb in total.

Hope this helps you somewhat.

---

### Post by OtonVM on 2006-05-28
Wow, that was fast! Thank you, most informative.

Except that with "extracted files" I actually ment where are the files first extracted, before beeing installed. For example, gentoo first compiles in /var/tmp, then moves the files. IF souch thing happens, obviously... :confused:

---

### Post by z_diver on 2006-05-28
> **OtonVM] I am planing a switch from gentoo to ubuntu on the 1st of june (or maybe the 2nd, depends on the seeds on bittorrent  said:**
>  The timing suggests you will be installing Dapper.  It's going to take a few weeks to work out a few bugs I'd imagine.  Please take that into consideration in the beginning.

[quote] Where are the applications stored? /usr/local or /opt (since they are precompiled). /usr/lib/
/opt is there but empty on my dapper system that I've been running for a month or so.
512 mb seems small for swap.  1.5 times ram is normal.  If you are concerned with speed, I hope you have more than 384mb of ram.   Also / partition can be 20 gigs or so with /home being 30gigs.  I have seen my / get up to 8gb or so but running "apt-get clean" takes it back down to 4.5 gigs usually.  Note: I'm not a gamer so that could effect your system.  

What is the reason for separate partions for /mnt/storage and /mnt/download unless they are separate physical disks?  If not and they will both be ext3, why not just make one mount point and one partition out of them.

btw, default for ubuntu is 2 partitions total.  / and /swap:D

Hope this helps and welcome to Ubuntu, hope it serves you well.

---

### Post by OtonVM on 2006-05-29
Ok, tnx!

Lol, I'm used to bugs, you can be sure of that... :) 
wow dude, I have 1 gig of ram and I never use a single kb of swap. An that's with bigger binaries. Without any -02 that should fly.
/mnt/storage and /mnt/download separated physically. Good to know about / remaining small, but never just two partitions. reiserfs for / and ext3 for other, maybe ext2 for /var and /tmp; the filesystem gets very fragmented in time. This way you can simply wipe them out and then restore the files.

---

### Post by jones_jj on 2006-05-29
I personally use reiserfs for all filesystems.  I have mine set up as /, /home, swap and one for /files, with everything else under /.  My /files is an LVM of 3 different hard drives.  That is something you may want to consider OtonVM.  Use LVM to combine both your downloads and storage partitions into one giant 235 GB partition called say storage.

---

### Post by OtonVM on 2006-05-29
[QUOTE=jones_jj]I personally use reiserfs for all filesystems.  I have mine set up as /, /home, swap and one for /files, with everything else under /.  My /files is an LVM of 3 different hard drives.  That is something you may want to consider OtonVM.  Use LVM to combine both your downloads and storage partitions into one giant 235 GB partition called say storage.[/QUOTE]

Ok, I agree, reiserfs is a great filesystem. But after some testing, I found out that ext3 beats it when dealing with large files or many smaller files. So I use reiser only for /, wich has neither. Same goes with logs, wich are beeing accesed and written to. With reiserfs I experienced higher cpu usage and longer access times. Moreover, ext3 is fully compatible with windows and oblivion loads much faster from it... ;) :D
About LVM; Does it combine only full hard drives (like raid) or also single partitions? Because /mnt/download is just half of the first 250GB sata disk, and storage is the other ATA 120GB disk. So I never considered it. It might be an idea... 

So, I'll start with this:
/dev/sda1 --- windows
/dev/sda5 --- windows data
/dev/sda6 --- /boot --- 100MB
/dev/sda7 --- / --- 20GB (as suggested)
/dev/sda8 --- swap --- 512MB (I seriusly belive that's more that enough)
/dev/sda9 --- /home --- 20GB
/dev/sda10 --- /var --- 8GB (for apt)
/dev/sda11--- /tmp --- 5GB (should be enough for a single-user system)
/dev/sda12 --- /mnt/download --- 120GB (It might even get bigger, up to 150GB, I belive)
/dev/hdc1 --- /mnt/storage --- 115GB

---

### Post by ifokkema on 2006-05-29
[QUOTE=OtonVM]Wow, that was fast! Thank you, most informative.

Except that with "extracted files" I actually ment where are the files first extracted, before beeing installed. For example, gentoo first compiles in /var/tmp, then moves the files. IF souch thing happens, obviously... :confused:[/QUOTE]

Well, as far as I know, the files are extracted right into place. If you download a .deb file, it will be:
- preconfigured (if necessary)
- unpacked (right into place)
- configured

[QUOTE=OtonVM]wow dude, I have 1 gig of ram and I never use a single kb of swap.[/QUOTE]
I have the same amount of memory and I've only used swap when putting a real high memory load on my system.

---

### Post by OtonVM on 2006-05-29
ok, thanks to everyone! I already feel confortable here. :)

---

