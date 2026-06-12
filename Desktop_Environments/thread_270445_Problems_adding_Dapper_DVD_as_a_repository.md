---
title: "Problems adding Dapper DVD as a repository"
date: 2006-10-03
forum: Desktop Environments
---

### Post by jujoje on 2006-10-03
Hi,

I'm trying to help a friend setup dapper on her pc. She doesn't have an internet connection, since her wifi card doesn't work out of the box. I sent her copy of the Dapper Drake DVD with the aim of installing build-essentials and other stuff required to get the wifi working. 

The problem is this: there are two drives: one cd-rw drive and one dvd-rw. The cd drive can't read dvds. Ubuntu was originally installed with Dapper CD from the cd-rom drive. I've tried adding the dvd as a repository, via the popup dialogue. It seems to add the packages fine, but then ignores the DVD and keeps asking for the CD when trying to install stuff. The precise steps I've done so far are: 

1. Insert Dapper dvd and add it as a repository via the dialogue box that pops up.
2. Updated the package database (sudo aptitude update)
3. Tried to install a package from the dvd (sudo aptitude install build essentials).
4. Get a message saying please insert Dapper cd-rom, despite the fact that the dvd is in the drive.
5. I have tried commenting out the line for the cd repository before adding the dvd repository and it stillkeeps asking for the cd and ignoring the dvd, looking in the cd drive rather than the dvd drive.

Is there any easy way to get ubuntu to look for the packages on dvd drive? I had a brief look at creating a local repository, but it seemed to be far more complex than should be necessary. I don't have access to her computer and it would involve me telling her all the commands by phone (she is in New Zealand and I'm in England).  Therefore as simple a solution as possible would be good.

Any help on this would be much appreciated

---

### Post by Alex.Gorban on 2006-10-04
Try to use [FONT="Impact"]**apt-cdrom**[/FONT] - APT CDROM management utility.

---

### Post by Ramses de Norre on 2006-10-04
Insert the dvd and run ```
sudo apt-cdrom add
```

---

### Post by jujoje on 2006-10-05
Thanks a lot, I'll give that a try :) 

I didn't even know there was such thing as apt-cdrom. Learn something new every day :-D 

cheers

---

### Post by jujoje on 2006-10-07
Unfortunately didn't work :-(

It seems to add the dvd okay but doesn't seem to see it when you try and install anything.

I though perhaps the easiest way to fix this would be simply to install edgy from the DVD, but unfortunetly the computer is a dell and doesn't allow you to boot from DVD (the drive is not selectable as a boot device in the BIOS).

---

### Post by CatKiller on 2006-10-07
Normally optical drives get tried in turn, even if only one of them is listed as an option.

---

