---
title: "Fake RAID device"
date: 2008-12-29
forum: General Help
---

### Post by CrimsonRider on 2008-12-29
Hi, I am trying to play around a bit with RAID5. I've got three 640gb discs, two of wich are connected to my system. I want to build a RAID5 array on those two discs, in effect creating a depecrated array and then add the third disc and have the raid array fixed.

I am trying this command;
```
mdadm --create /dev/md1 --level=raid5 --chunk=128 --raid-devices=3 /dev/sda2 /dev/sdb2 --force
```

But then I get this error;
```
mdadm: You haven't given enough devices (real or missing) to create this array
```

Now I know that indeed, the third disc, sdc, is not there, and I can't use it right now, but still I want to be able to create this array. Is there some way to use a fake /dev device or such?

I tried searching, but that mainly gives a lot of fakeraid information, and that isn't very helpfull.

---

### Post by fjgaude on 2008-12-29
Okay, in your create line, take out the --force and simply replace it with the word **missing**. That will do it.

---

