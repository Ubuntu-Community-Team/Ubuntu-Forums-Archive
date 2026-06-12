---
title: "Why does Transmission-gtk lose data all the time"
date: 2012-06-20
forum: Desktop Environments
---

### Post by Acharn on 2012-06-20
I wasn't sure which forum to use, this or the Absolute Beginner's forum, but I decided to try this one first. I've been using the Transmission fit-torrent program since last year. I'm pretty much satisfied with it, it seems reasonably fast and it's easy to add torrents. The thing is, I've noticed that every few days torrents which I thought were completely downloaded suddenly appear in the "Paused" section. Often they suddenly show up in the "Errors" section, either with "Bad file descriptor" or "Verify local data." Where they were complete, now they show only 87% or 99% complete. It seems to happen to about 20% of the torrents I downloaded.

So I was wondering, is this a regular occurrence with Transmission? Is this a feature? Or should I be reporting a bug? It generally just requires clicking on "Verity local data" or starting the download over, but it's annoying.

---

### Post by 3Miro on 2012-06-20
I have never seen this behavior. What is your HDD arrangement, there may be an issue with storing the files to the partition that you are using due to the filesystem problem or mechanical problem with the HDD.

---

### Post by Acharn on 2012-06-20
Well, let's see. Here's the output from 'df -h':
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        24G  6.2G   16G  28% /
udev            491M  4.0K  491M   1% /dev
tmpfs           201M  884K  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            501M  160K  501M   1% /run/shm
/dev/sda3       438G   77G  339G  19% /home

```
There's also a 5GB swap file in sda1. I save all torrents to various directories in /home, on sda3.

Checking Transmission for the first time thismorning, I find two torrents which were complete yesterday listed in the "Paused" group with messages, "Error: Please verify local data! Piece #xxx is corrupt." The same two torrents are also listed in the "Error" group with the same error messages. Hmmm. Interesting. Yesterday there were about ten in the paused group and four in the error group, all of which were reported as completed before I shut down last night, including these two.

---

### Post by panaut0lordv on 2012-06-24
This is happening to me all the time. Transmission 2.51 (13280) here.

---

### Post by Acharn on 2012-06-24
Yes, that's the version of Transmission I'm using now, but this is not new. I started using Ubuntu (and Transmission last year in September, and it's always done this. However I was having hard drive failure problems, and then trying to use "persistent sessions" with a USM bemory stick and frequently losing my whole setup. I expected after getting my new hard drive it would stop.

I have found part of the problem. There were some audio torrents I downloaded. I included them in my music library, but was still uploading them. However, a couple of them were lacking ID3 tags, which I entered with EasyTag (a very good program). Apparently Transmission periodically compares the torrent files on my computer with other torrent files and considers any change corruption. Actually that makes sense; it normally should. So I remove those torrents from Transmission now before I edit the tag info. Still doesn't explain what's going on with movie and video files that I don't edit in any way.

---

### Post by Acharn on 2012-06-24
Yes, that's the version of Transmission I'm using now, but this is not new. I started using Ubuntu (and Transmission) last year in September, and it's always done this. However I was having hard drive failure problems, and then trying to use "persistent sessions" with a USM bemory stick and frequently losing my whole setup. I expected after getting my new hard drive it would stop.

I have found the solution to part of the problem. There were some audio torrents I downloaded. I included them in my music library, but was still seeding them. However, a couple of them were lacking ID3 tags, which I entered with EasyTag (a very good program). Apparently Transmission periodically compares the torrent files on my computer with the same  torrent on other seeders and considers any change corruption. Actually that makes sense; it normally should. So I remove those torrents from Transmission now before I edit the tag info. Still doesn't explain what's going on with movie and video files that I don't edit in any way.

---

