---
title: "Thunar: cut&amp;paste through a symbolic link will cause data loss"
date: 2011-09-15
forum: Desktop Environments
---

### Post by tanoloco on 2011-09-15
Hi all,

I would like to inform you I found a behaviour of Thunar which can cause data loss, just to avoid other people to loose data as in my case.

I know it's not soooo common to jump into this, but it can always happen.

Let's say I simply wanted to move a file from a folder A to a folder B.

The error was that in the past I created a symbolic link under my home folder pointing to the B folder, and I named it ~/B ... but I wrongly created it so that it points to A folder and not to B.
So I had a symbolic link named ~/B pointing to A folder :(

I used Thunar to cut & paste a file from A to B folder: I went to A folder and right-clicked on my file and chose *cut*, then I went to my symbolic link under my home ~/B thinking it was the B folder when actually it was the A folder itself!
I right-clicked and chose *paste* ... 

Ok: a window advised  me that there was already a file in the destination folder with the same name, but this was expected to be because B can contains many files in common with A.
So I chose *replace* and my original file was just removed.

The result was that I lost my files!

I tested this on Nautilus Elementary and PCManFM too and this was not found: they keep a copy of the file as it might be.

Here's the report on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/851018]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/851018")

Cheers

---

