---
title: "dfi lanparty sata raid"
date: 2007-08-28
forum: Desktop Environments
---

### Post by zuper on 2007-08-28
hi,

before i start asking my "stupid" questions, i want to say thank you to everybody helping out in this forum!!

i've got a problem since my first installation on ubuntu 7.04 x64 (a couple of days ago :))

I have 2 sata disks in raid 0 where i keep the xp installation and all my files.
I added a pata disk where i put ubuntu (leaving the others connected during installation)

how can I actually see the files on the raid? i mean r/w acces of course.

I've tried anything read on the internet...

ntfs-3g gives me some errors...

i read about using dmraid, but i'd like to have some good explanations, because i'd like not to destroy any disk :)

thank you guys!!

PS: do you think i made a great deal installing x64? i already had some problems like flash player, skype, google earth...which fortunately i managed to solve, but i was thinking on reinstalling x386 version...just to make it easier to learn, what do you think?

---

### Post by kuja on 2007-08-28
Yeah, you'll have to use dmraid to be able to read the stuff on the FakeRaid ..... look up the FakeRaidHowto on google (it should be the first result(funny how searching with google is faster than searching with the ubuntu wiki search feature eh?)) 

I don't think you'll run into any real issues with the x86_64 version really. Most stuff that requires effort in the x86_64 version also requires effort in x86 too. (That being said, there's not really that much more there to learn, honest!)

---

### Post by zuper on 2007-08-28
i've seen that guide, but i understood that it's just to install it on a raid system.

what i'd like to do is see what there already is on the raid.

just mount them ;)

---

### Post by kuja on 2007-08-28
No, you need to have dmraid installed even to look at what's in the raid. Granted, now that I think about it; all you'll need to do is install dmraid and ntfs-3g, mount it .... and you should be good to go. I think.

---

