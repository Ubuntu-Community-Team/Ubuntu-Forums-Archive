---
title: "Need to erase -old- /usr after moving it"
date: 2009-01-30
forum: General Help
---

### Post by Geobot on 2009-01-30
I've been using Ubuntu on my netbook for about 2 months now, and I ran out of room on my main drive. My original setup was bad in retrospect, since I got bad advice on how to set up the partitions:

sda1  /      (4GB)
sdb1  /home  (16GB)

So, after messing with it for a bit, and a bit of learning about fstab and vi, and playing with my Live CD.... I finally got my setup like this:

sda1  /      (4GB)
sdb1  /home  (8GB)
sdb2  /usr   (8GB)

Which is exactly how I want it... except for one problem. Since I tar'd/copied my /usr folder over to the new partition and mounted, everything works like a champ, but I can't figure out how to erase the old /usr folder, on the sda1 partition.

Of course, if I simply try to navigate to the /usr folder, it gives me the one on the sdb2 partition. It does this in a terminal, browser, whatever. I just can't seem to get to the old folder.

My question is this: How in the world can I erase the old /usr folder from the sda1 partition and clear up 2GBs of space?

---

### Post by louieb on 2009-01-30
The /usr  folder is still the mount point for partition sdb2. Don't delete it.

To free up the disk space  on sda1 use the live CD  to empty the contents of the /usr folder on sda1. 

To play it safe boot a live CD and rename /usr to /usrold or something like that and create a new /usr folder on sda1. Then reboot to the hard drive install  if it boot normally you know its using /usr on sdb2. Then you can delete /usrold and free the space. 

Let us know how it goes.

---

### Post by Geobot on 2009-02-01
Ok, so I got it all working right now, after ending up even more confused than before. Thanks for the idea of renaming my old /usr, though, because it saved me a heart attack, I think.

Basically, what I did was this:

I booted with a Live CD, and renamed my /usr on sda1 to /usrold. Then I booted normally, and it gave me all kinds of "file not found errors and wouldn't start the X-server. Of course, me not knowing any better, decided that it must be because my new /usr on sdb2 wasn't mounted. So I poked around at my fstab for a bit over an hour, and couldn't figure out why it wouldn't mount.

In the end, it turned out to be something very simple, but enlightening to me, since I'm new at the nix game. On sda1, which is my root partition, I had renamed the /usr folder to /usrold, so I didn't have a folder named /usr to mount sdb2 to. All I had to do was make an empty folder and everything came out fine.

All in all, I'm satisfied with the learning experience, considering if I was still running Windows I'd have just said 'screw it' and formatted/reinstalled from the ground up.

Thanks for the help!

---

### Post by dcstar on 2009-02-01
> **Geobot said:**
> I've been using Ubuntu on my netbook for about 2 months now, and I ran out of room on my main drive. My original setup was bad in retrospect, since I got bad advice on how to set up the partitions:

sda1  /      (4GB)
sdb1  /home  (16GB)

So, after messing with it for a bit, and a bit of learning about fstab and vi, and playing with my Live CD.... I finally got my setup like this:

sda1  /      (4GB)
sdb1  /home  (8GB)
sdb2  /usr   (8GB)

Which is exactly how I want it...
.......

You really shouldn't move system partitions, you would have been a lot better off just increasing the size of the root partition.

The /usr partition has nothing that a user should touch, it is for installed user **programs** and the resources they require.

Having a separate /home partition is fine (far better than the "standard" install), but now you have a system that is going to complicate things if the /usr partition ever has a problem or you want to do certain types of version updates.

---

### Post by heindsight on 2009-02-01
> **dcstar said:**
> You really shouldn't move system partitions, you would have been a lot better off just increasing the size of the root partition.

The /usr partition has nothing that a user should touch, it is for installed user **programs** and the resources they require.

Having a separate /home partition is fine (far better than the "standard" install), but now you have a system that is going to complicate things if the /usr partition ever has a problem or you want to do certain types of version updates.

In the last 7 or so years I've always had my /usr on a separate partition and it never caused a problem and I can think of no reason why it should.

If you have limited space on the disk containing / then having /usr on a separate partition makes a lot of sense - otherwise you're likely to run out of space to install new programs.

---

### Post by Geobot on 2009-02-02
> **dcstar said:**
> You really shouldn't move system partitions, you would have been a lot better off just increasing the size of the root partition.

The /usr partition has nothing that a user should touch, it is for installed user **programs** and the resources they require.

Having a separate /home partition is fine (far better than the "standard" install), but now you have a system that is going to complicate things if the /usr partition ever has a problem or you want to do certain types of version updates.

The reason I didn't want it on my root partition is because the drive it's on is only 4GB, so obviously it fills up when you start installing programs. When I got a "disk full", it needed to go somewhere else.

Even though I've only been using Ubuntu for a couple months, I've already learned my way around a bit, and I have a long history with computers in general. Don't worry, the /usr is safe with me.

---

