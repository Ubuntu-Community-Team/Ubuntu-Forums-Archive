---
title: "Read Only Filesystem"
date: 2010-06-28
forum: Desktop Environments
---

### Post by adamg2000 on 2010-06-28
I have an hfsplus HDD that was previously attached to my MacBookPro. Something went wrong and the Mac could no longer see it. I put it in another enclosure, which it also couldn't see. I put it inside my Ubuntu (Karmic) box and guess what, it mounted no trouble. However, some of the files (family photos :( ) cannot be opened as I browse using the visual filesystem (due to permissions not being detected I think), so I tried in Terminal to change the owner etc using sudo chown. I get the following response (001.jpg being an example of many):

chown: changing ownership of `001.jpg': Read-only file system

ls -l brings this up

-rw------- 1 99 99  176577 2008-10-26 02:46 001.jpg

Can anyone please offer some assistance as to how I might free these up? I'm quite a newbie. Searching around the net has shed some light but as yet no solution.

---

### Post by mikewhatever on 2010-06-28
The problem seems to be not with the file but rather with the file system. When there are errors in the file system, Ubuntu will often mount it as read only. Have you tried running a file system check?

---

### Post by GlazedWicker on 2010-06-28
Ubuntu can not write to hfs+ filesystems... at least there's no way that I know of.

---

### Post by aphatak on 2010-06-28
Ubuntu might not be able to write to it, but you can still copy them - with sudo if necessary.  The copies belong to you, to do what you would with them.

---

### Post by adamg2000 on 2010-06-28
Thanks guys, collectively you've helped me crack it. I assume because I cannot write to it, I cannot change the permissions, but using sudo in terminal I can copy them to other drives in the system, and in those drives I can change the permissions to something I can use. It works.

Problem Solved!

---

### Post by toffuuu on 2010-08-20
Ok i will be this weekend starting to be using Ubuntu after i build my Quad Core PC, I just tho want to be sure since i have some drivers i want/need for ubuntu on my HFS+ external HDD that i now currently use on my MBP,  with no problems with it as far as I know,  should be able to @ least still read it??  and also to install drivers from it?  sorry if this is slightly off topic  but Its a question i been racking my head on  for a bit  and trying to find info on...

---

