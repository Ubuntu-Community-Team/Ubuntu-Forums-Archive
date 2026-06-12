---
title: "mounted hdd keeps erasing content"
date: 2009-01-06
forum: General Help
---

### Post by shortridge11 on 2009-01-06
I'm running 8.10 desktop, but i don't really use the gui.  I just ssh in to do what i need to.  For some reason, one of my mounted hdds keeps erasing itself and disappearing and reappearing.  I mounted the hdds by their UUIDs, and i'll include that code below.  Anyone know what might be causing this? If not i think i'll just do a clean reinstall.  Also, I'm using xfs as my file system for all these hdds (they hold larger files, some over 10gigs a piece).  I know ext4 just became stable.  Should i stay with xfs or make the switch?

```
usr@xxxxxxxxx:~$ sudo vim /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc              /proc          proc  defaults             0  0
# /dev/sdc2
UUID=ffe4990f-3825-42a5-be41-0fbeb7028a1d  /               ext3  defaults,errors=remount-ro  0  1
# /dev/sdc1
UUID=b8d517c1-ac84-42cd-8b49-a297afc918dc  none            swap  sw                          0  0
# /dev/sda1 -
UUID=264db609-d576-4ebf-bd31-5b3dce9db897  /media/XX2       xfs   defaults   0  0
# /dev/sdb1
UUID=d9c6a51f-d2a6-470c-9003-74360b4a9f2e  /media/XXXXXXX3   xfs   defaults   0  0
# /dev/sdc3
UUID=49f80168-76b9-4180-bf31-17286a261130  /media/XX        xfs   defaults   0  0
# /dev/sdd1
UUID=01cae850-1ce5-4744-a08d-356f921d2619  /media/XXXXXXX1   xfs   defaults   0  0
# /dev/sde1
UUID=384e7f22-7265-475a-9509-28f2384945d5  /media/XXXX      xfs   defaults   0  0
# /dev/sdf1
UUID=eb6a8b74-7f33-404c-8d3d-7c2eb1a184c0  /media/XXXXXXX2   xfs   defaults   0  0

```

---

### Post by hangfire on 2009-01-06
> **shortridge11 said:**
> I'm running 8.10 desktop, but i don't really use the gui.  I just ssh in to do what i need to.  For some reason, one of my mounted hdds keeps erasing itself and disappearing and reappearing.  I mounted the hdds by their UUIDs, and i'll include that code below.  Anyone know what might be causing this? If not i think i'll just do a clean reinstall.  Also, I'm using xfs as my file system for all these hdds (they hold larger files, some over 10gigs a piece).  I know ext4 just became stable.  Should i stay with xfs or make the switch?
[/CODE]

Losing partitions can mean overlapping partition (partitioning errors). Mounts coming and going usually mean automounter interference. Check out your /etc/auto* files. A bad or poorly supported IDE/SATA controller might be the problem. If it is, you will have the same problems with any file system.

I don't know what losing content means. Are whole files disappearing?

Are there ugly read/write errors in /var/log/*?

XFS is fast and great for temp files, such as audio/visual intermediate files than can be regenerated from primary source if a partition is lost. It is also useful for very intelligent databases that manage their own integrity to a very fine level. I have used it in both instances without any loss of data and a measurable gain in speed over ext3. I do not use it for primary file systems (root, home) except for throwaway embedded or virtual clients that can be easily reimaged. In this case, redundancy is provided by having more than one client.

For primary filesystems, you should be using Reiser or ext3, or maybe ext4, I don't know, haven't tried it yet.

-HF

---

### Post by shortridge11 on 2009-01-06
I currently use ext3 for my root, xfs is strictly for storage.

---

### Post by shortridge11 on 2009-01-08
apparently ext4 is stable now, so i'll be using that soon.  I didn't get any output with
ls | grep auto

and i looked through my logs and didn't see anything.  Anyone know what would cause a HD to randomly dump everything and then appear not mounted?  Right now It's not appearing as mounted, but i can access it....for some reason...

please help me avoid a reinstall

---

### Post by shortridge11 on 2009-01-08
Some more info about the drive that keeps disappearing.  It's a 500Gig drive , and it's called sdb1 in my earlier post.

---

### Post by hangfire on 2009-01-08
> **shortridge11 said:**
> Some more info about the drive that keeps disappearing.  It's a 500Gig drive , and it's called sdb1 in my earlier post.

I noticed it is on /media, does that mean it is a USB drive?

I had a similar problem with a USB key, it turned out that the USB hub inside my ViewSonic monitor went to sleep with the rest of the monitor. Everything downstream, including a mouse and USB key, went away and came back each time. :(

If the 500G drive is USB mounted, try a different USB port, one without a built-in hub or an external USB hub (direct).

If it is an internal drive on SATA or IDE, you have problems. It should not be on /media, which is an automount mount point. Manually editing /etc/fstab and giving it a more permanent place to mount might fix it. There are probably Gnome or KDE gui's to do this, but I rarely use those.

-HF

---

### Post by shortridge11 on 2009-01-08
This computer is a personal server backup....I have 6 500Gig drives (internal, sata) and I'm very very sure they should be mounted in /media/ for that reason.  They hold my media files like my home movies, etc

---

### Post by dcstar on 2009-01-08
> **shortridge11 said:**
> This computer is a personal server backup....I have 6 500Gig drives (internal, sata) and **I'm very very sure they should be mounted in /media/ for that reason**.  They hold my media files like my home movies, etc

NO. /media is a SYSTEM directory for mounting external media, it is not for users to place their stuff in.

You have the whole /home/ tree for user data, I suggest you place your personal mount directories there, or create a new tree somewhere else if you want to share data - just don't use system directories because a name appears convenient.

---

### Post by shortridge11 on 2009-01-08
I'm pretty sure any extra mounted drives should be mounted in /media......  i've used ubuntu long enough to know you shouldn't need to do a total reinstall for 99.999 of things, but i'm still considering a reinstall. If someone can completely help me solve this problem i will have my children sing your name throughout our household for ages to come. stories will be told.

---

### Post by dcstar on 2009-01-08
> **shortridge11 said:**
> I'm pretty sure any extra mounted drives should be mounted in /media......  i've used ubuntu long enough to know you shouldn't need to do a total reinstall for 99.999 of things, but i'm still considering a reinstall. If someone can completely help me solve this problem i will have my children sing your name throughout our household for ages to come. stories will be told.

If you have one drive that is causing problems, then install the smartmontools package and use the tools to determine the health of the drive.

---

### Post by hangfire on 2009-01-09
> **shortridge11 said:**
> I'm pretty sure any extra mounted drives should be mounted in /media......  i've used ubuntu long enough to know you shouldn't need to do a total reinstall for 99.999 of things, but i'm still considering a reinstall. If someone can completely help me solve this problem i will have my children sing your name throughout our household for ages to come. stories will be told.

I fully agree with **dcstar**. The ***/media*** directory is monitored, and managed by the system for mounting external (that is, Removable) media.

You can prove that to yourself by seeing if you get unwanted unmounts there. Oh wait, you already do....

I'm not too keen on mount points on mount points (on my systems, /home is a mount point). I suggest creating some top-level mount point directories, e.g.:

/mymedia1
/mymedia2
/mymedia3
...

Edit your /etc/fstab and put your internal devices there. Let /media alone for the system to put USB drives and digital cameras there.

Or, keep doing what you are doing and head straight for a reinstall. You've already received good advice, now it's up to you....

-HF

---

### Post by hangfire on 2009-01-09
...

---

### Post by shortridge11 on 2009-01-10
Ahh thanks. I had no idea. I thought you were supposed to mount all those in /media. I will change that immediatly.

---

### Post by hangfire on 2009-01-12
> **shortridge11 said:**
> Ahh thanks. I had no idea. I thought you were supposed to mount all those in /media. I will change that immediatly.

Tell us how it goes, and if all is well, please mark the thread as Solved in Thread Tools.

-HF

---

### Post by shortridge11 on 2009-01-27
meh, the problem remains, i think it's a hardware issue, but thanks for the advice on mounting, consider this solved =\

---

