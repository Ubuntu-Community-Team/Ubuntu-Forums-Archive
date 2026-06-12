---
title: "Thunderbird profile on Dropbox, &quot;conflicted copies&quot;?"
date: 2010-12-23
forum: Desktop Environments
---

### Post by gogolink on 2010-12-23
Hi,

I'm running 10.10 on two computers, and I'm using **Dropbox** to keep **Thunderbird** synced.  

(I created a subfolder "ThunderbirdProfile" in my Dropbox folder, moved the contents of [random-letters-and-numbers].default (in /home/[username]/.thunderbird) there, and modified the file **profiles.ini** (also in /home/[username]/.thunderbird): I changed the value of "IsRelative" from 1 to 0, and the Path to /home/[username]/Dropbox/ThunderbirdProfile.)

Syncing works basically fine: I have the same Thunderbird address books, calendars (Lightning extension), and folders on both computers.

But there's one problem: Thunderbird keeps creating "conflicted copies" of various files (I guess because I often open Thunderbird before Dropbox is done syncing), and these copies quickly eat up a lot of my valuable space on Dropbox.  I do delete these files occasionally, but I wonder whether there's any way to either keep Thunderbird from creating them in the first place, or delete them automatically (a script that runs at startup?).
Or is there a more elegant way to sync Thunderbird across two Ubuntu computers - one that doesn't involve keeping the entire profile folder on Dropbox?  (I'd be happy to use Ubuntu One, but I don't know if there's anything different I could do with it, given that I'm not using Evolution.)

Any ideas would be much appreciated.

---

