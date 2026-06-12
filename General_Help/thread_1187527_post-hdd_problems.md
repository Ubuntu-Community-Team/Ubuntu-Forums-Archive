---
title: "post-hdd problems"
date: 2009-06-14
forum: General Help
---

### Post by iAndrew on 2009-06-14
Alright, if this isn't the correct forum to post this problem in, please move it accordingly. Thanks.

--

So I took my laptop to school in my backpack, and must've not set it down lightly once or more so I assume that the dropping of the laptop may have done some hdd damage.

Anyways, I bring it home and try to turn it on and I get stuck on wallpaper w/o with no top bar / bottom bar or icons showing.

Few days later I turn it on and it works.

To be safe, I decided it'd be very smart to run a chkdsk-ubuntu-equivalent to make sure that the hdd isn't faulty or I won't have future problems like that, and I'm not very sure where to start.

I read/searched up and go to fsck and a few parameters, but I have to unmount my main drive and I want to know if that's what I have to do or boot it off a liveCD or whatever other options maybe out there.

---

### Post by Cheesemill on 2009-06-14
You best bet is probably to boot the Live CD and then run fsck from there.

---

### Post by iAndrew on 2009-06-14
Thanks, I'll do this.

Resolved ~

---

### Post by CatKiller on 2009-06-14
Otherwise, ```
sudo touch /forcefsck
``` and reboot.

---

