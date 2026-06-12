---
title: "how to cd to /dev/sdb!?"
date: 2009-03-13
forum: General Help
---

### Post by artheus on 2009-03-13
Hi!

I just recently bought a new external HDD which I want to use with my VSFTPD and my APACHE2.

But I am a noob. And can just not seem to find the path to my external hdd.

I know it has the device name /dev/sdb1
And there is only one partition on it.

I used Parted to make a partition on it.

My Ubuntu is Ubuntu Server Edition 8.10 32-bit.

Cheers,
Artheus

---

### Post by kanikilu on 2009-03-13
I think you need to mount it first.
```
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
```
Obviously add other mount options as appropriate.

---

### Post by artheus on 2009-03-13
Thanks!
Will I have to write that in somewhere for the Server to do this everytime it restarts?

---

### Post by taurus on 2009-03-13
You don't access /dev/sdb1.  Instead, you mount /dev/sdb1 to somewhere, mount point, and access (write) the mount point.

What filesystem did you format /dev/sdb1 to?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

p.s.  Just add an entry to /etc/fstab if you want it to mount each time you boot your machine.

---

### Post by Neo_The_User on 2009-03-13
Try checking in the /media folder as all my sdb devices show up there.

---

### Post by artheus on 2009-03-13
I formatted it to ext3
and I set it as a primary drive

Thanks.

using "sudo mount /dev/sdb1 /mnt/sdb1"
it says I've got to specify the filesystem. How would I do that?

And what changes do I have to do to make the Ubuntu server do this automatically every time it starts?

---

### Post by Neo_The_User on 2009-03-13
> **artheus said:**
> I formatted it to ext3
and I set it as a primary drive

Thanks.

using "sudo mount /dev/sdb1 /mnt/sdb1"
it says I've got to specify the filesystem. How would I do that?

And what changes do I have to do to make the Ubuntu server do this automatically every time it starts?

You edit /etc/fstab. Follow this gentoo guide on how you would do so.

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=8](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=8)

I recommend using the "noatime" function so it will boot faster.

---

### Post by artheus on 2009-03-13
In the media folder I get only the cdrom.

(btw. I have not installed the GUI, and do not want to do so)

---

### Post by taurus on 2009-03-13
If you want to mount /dev/sdb1 to /media/sdb1 automatically upon boot, edit /etc/fstab

```
sudo nano -Bw /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   2
```
Save it.  Then, create a new mount point, /media/sdb1, unless you want to mount it to /mnt/sdb1 (which means you need to modify to the entry above).

```
sudo mkdir /media/sdb1
```
Reboot.

---

### Post by Neo_The_User on 2009-03-13
> **taurus said:**
> 

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   2
```


@OP, ext4 is much quicker than ext3. I recommend using tune2fs to change the filesystem to ext4 if you haven't already.

---

### Post by kanikilu on 2009-03-13
> **taurus said:**
> Reboot. Just a little addendum - I would try ```
sudo mount -a
``` before you reboot, just to make sure it works and that you didn't make a mistake...

---

### Post by artheus on 2009-03-13
Thank you all!

Great help :D

---

### Post by Neo_The_User on 2009-03-13
> **artheus said:**
> Thank you all!

Great help :D

No problem.

---

### Post by Slim Odds on 2009-03-13
> **Neo_The_User said:**
> @OP, ext4 is much quicker than ext3. I recommend using tune2fs to change the filesystem to ext4 if you haven't already.

That would be asking for trouble......

---

### Post by artheus on 2009-03-13
Well.. something must have gone wrong...

Cause.. everytime I restart now. It says as usual "server login:"

and I write my username.. But when I hit Enter... It says "bash: username: command not found.

And it now looks as though I am logged in as "root@server:~#"

and when I write eg. "cd /mnt/sdb1" it says "Password:"
so I write in my password: "password123" and hit Enter.
Output : "bash: password123: command not found"

What!? o_o

Help me?

---

### Post by artheus on 2009-03-13
No matter!

Shutting down, and starting up again (instead of restarting) helped!

TANKS ALOT! :)

Artheus

---

### Post by artheus on 2009-03-13
**One more thing!**

Now I've gotten it to work perfectly with vsftpd thanks to you all! :) And that I am very happy about!
There is only one thing now.

When I log in as a Virtual user with some ftp-client to this.. I will be in the /mnt/sdb1/username. But I can without any problems go to any other folder on that computer. So the Virtual User is not restricted to just that folder.

Could I restrict a Virtual User in vsftpd to only one folder, which they can do with as they please?

And.. is it possible to restrict the maximum size of that folder?

Cheers!
Artheus

EDIT:

Managed to use the chroot_local_user.
And I put the write_enable to yes

but.. now my users can't make folders or anything. What should I do?

---

