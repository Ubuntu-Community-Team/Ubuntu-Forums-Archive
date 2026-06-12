---
title: "Can't do anything with a partition"
date: 2009-01-19
forum: General Help
---

### Post by oopsie on 2009-01-19
I only gave Ubuntu a little room when I installed it, because I just wanted to test it out.

That room is now full, so I wanted to add more.

I freed up some room from Windows, formated it the way Ubuntu likes it and mounted it, but Ubuntu can't do anything with it. I can't copy files to it, or make folders or anything.

Anyone know what I'm doing wrong?

---

### Post by blackened on 2009-01-19
Run gparted from the livecd, unallocate the new partition you created, then grow the partition where / is mounted to use the unallocated space.

---

### Post by oopsie on 2009-01-19
> **blackened said:**
> Run gparted from the livecd, unallocate the new partition you created, then grow the partition where / is mounted to use the unallocated space.

Can't do that

---

### Post by blackened on 2009-01-19
> **oopsie said:**
> Can't do that

Which part?

---

### Post by oopsie on 2009-01-19
The drive Ubuntu is on, is full. No room to grow anything.

The spare room I made is on a different drive.

---

### Post by oopsie on 2009-01-19
So, basically. Despite me asking all over the place and reading all sorts of guides, manuals and forums. There are zero ways of making Ubuntu access the 50GB I freed up for it?

I see.

Well, Ubuntu is pretty useless with this small amount of space, so I guess it's the end of my Ubuntu experiment.

It was an interesting two weeks.

Cya!

---

### Post by setsanto on 2009-01-19
at the top right there is a menu where you can select what hard disk drive you are looking at.

~Setsanto

---

### Post by blackened on 2009-01-19
Sorry, I lost my psychic abilities in a hunting accident years ago.

It's best if you provide all the necessary details about a problem before asking for help with it.

All obtuseness aside on both our parts, back to the problem:

so the partition you have Ubuntu on is too small. I understand that much. How big is the *drive* that Ubuntu is on though? Is it the only thing on that drive?

I also understand that you have Windows on a second drive and that you've shrunk its partition and created an extra ext3 partition in the freed space that you now wish to mount part of the root filesystem to. This is completely possible, but fiddly in practice.

How bout you give us an exact layout of all partitions, including sizes and types, on both drives so that we may understand it all a bit better.

---

### Post by oopsie on 2009-01-19
I have a 27GB drive. It's about 20GB full.

I have a 80GB drive. Windows is on it. Linux is on it. It has about 1-2GB free.

I have a 300GB drive. 100GB is used. 200GB isn't. I freed up 50GB and am trying to give that to Ubuntu.


Everything Ubuntu related is currently squished into a 10GB of space I gave it on my 80GB drive two weeks back.

And it's hard for me to give the relevant information when I don't know what IS relevant information.

---

### Post by logos34 on 2009-01-19
> **oopsie said:**
> 
I have a 300GB drive. 100GB is used. 200GB isn't. I freed up 50GB and am trying to give that to Ubuntu.

Everything Ubuntu related is currently squished into a 10GB of space I gave it on my 80GB drive two weeks back.


follow this:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Or turn it into a separate /home (see link in my signature)

---

### Post by blackened on 2009-01-19
> **oopsie said:**
> And it's hard for me to give the relevant information when I don't know what IS relevant information.

You're right, I apologize for my impatience.

You have three options that I'll list in order from easiest and least risky to hardest and riskiest:

1. Shrink the Windows partition on the 80Gb drive and grow the Linux partition into the space it left behind.

2. Keep the 80Gb drive as-is and move /home to a partition on one of the other drives.

3. Keep the 80Gb drive as-is and move /usr to a partition on one of the other drives.

I suggest doing #1. Absolutely the easiest and least likely to trash your system.

#2 is doable, but probably won't benefit you much on a new system considering your home directory has next to nothing in it.

#3 would benefit you greatly on a new system because this is where the bulk of large system files reside (besides logs, obviously), but by moving it you run a very high risk of breaking many things (e.g. symlinks) if not done correctly.

---

