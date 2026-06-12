---
title: "move \home"
date: 2008-09-11
forum: Desktop Environments
---

### Post by antknee869 on 2008-09-11
Ok, I have read a few tutorials on how to do this, and tried it with disastrous results.
I simply want to move the /home folder to a new hard disk I just installed and keep the /home name. The new hard disk mounts fine.
I also want to make sure that any other user's accounts home folder defaults here.
Thanks

---

### Post by fishonadish on 2008-09-11
Hi,

Mount the new drive (e.g. 'mount /dev/sdb1 /mnt') and copy over your current /home/user to /mnt/user.
Then add a new line to /etc/fstab for the new drive (the will be something like ' /dev/sdb1 /home ext3 relatime 0 2', assuming its an ext3 filesystem, and sdb1 is the new drive).
When you reboot, you'll need to change the permissions of your new home directory so that your user owns them.  As root, do:

chown -R USER /home/USER
chgrp -R GROUP /home/USER

(Your primary group is probably the same as your username).

Your old /home/USER folder will still be there on the first drive, but not visible in the file system.  If you need to free up this space, you could mount the drive from a live CD and delete it.

Best of luck.

Fishonadish

---

### Post by Malac on 2008-09-11
I used aysiu/psychocats method ages ago and it worked purrfectly [sic]

Here's the link:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Hope this helps.

---

### Post by antknee869 on 2008-09-11
Yeah, I used that too and it torched my profile. When I logged on it said the home directory couldn't be found and then my userid didn't own it or have write permissions.
Thanks

---

### Post by Malac on 2008-09-12
> **antknee869 said:**
> Yeah, I used that too and it torched my profile. When I logged on it said the home directory couldn't be found and then my userid didn't own it or have write permissions.
Thanks
Sorry about that, that's unfortunate. I can only assume that you may have mis-typed a command as it worked first time for me with no problems.
Sounds like an /etc/fstab error maybe. And/or your permissions weren't copied over too.

I usually try to cut and paste all commands from howto's into the terminal rather than type them in myself, making only alterations for /dev/sd..., and that sort of thing, on my system. The trouble is you need to be root for a lot of the commands so if you get your /dev/sd<whatever> one letter/number out then it will just do it, only when you reboot do you realise that you wanted the second partition but put in /dev/sda1 as per instructions.

---

### Post by antknee869 on 2008-09-12
I'm sure I did something wrong. I think it wanted to use the whole disk as /home instead of just the folder I created. 
I will give it another spin and see what happens.

---

### Post by Malac on 2008-09-12
> **antknee869 said:**
> I'm sure I did something wrong. I think it wanted to use the whole disk as /home instead of just the folder I created. 
I will give it another spin and see what happens.
Tip:
Print of the instructions in full and have them to hand during the reboots and so on, then you can tick off each step so you don't miss out anything.

Good Luck, let us know how it went.
Any problems, I'll try and help.

---

### Post by bench on 2008-09-15
I don't think you can just move home to a seperate disk without changing the location of each users home dir.  You need either a whole disk or a whole partition you can mount as /home.  The only other option is to use something like LVM to extend the root partition onto that extra disk.

I did by using tar to create an archive of each user's home, then extracting the tarballs onto the new disk.

eg. in /home

sudo tar cvf <username>.tar <username>

then with my new disk mounted on /media/target

cd /media/target
sudo tar xvf /home/<username>.tar

then 

sudo umount /media/target
sudo mv /home /oldhome
sudo mkdir /home

then edited the fstab to mount my disk /dev/sda<X> on /home

then

sudo mount /home

After a couple of reboots, once I was happy all was well, I deleted /oldhome.

Hope this helps if you're still stuck.

---

### Post by HacDan on 2008-09-15
> **antknee869 said:**
> I'm sure I did something wrong. I think it wanted to use the whole disk as /home instead of just the folder I created. 
I will give it another spin and see what happens.

As far as I know, and I could be very wrong, but I'm almost positive that you can't just move /home to a new folder. At least not in that aspect. You have to mount the said hdd in the filesystem at /home. I know that would be the easiest way, and the previous post should help for moving the information of the users directories to the new hard drive. I hope that helps and clears things up for you.

---

### Post by fishonadish on 2008-09-20
> **antknee869 said:**
> When I logged on it said the home directory couldn't be found and then my userid didn't own it or have write permissions.
Thanks

That's why you need to reset the permissions of the new home folder with:

chown -R USER /home/USER
chgrp -R GROUP /home/USER

Otherwise, since you copied them as root, they'll belong to root.

Fishonadish

---

### Post by antknee869 on 2008-09-20
Yeah, I guess I missed that in the directions.
Thanks

---

### Post by anars on 2008-09-23
> **fishonadish said:**
> Hi,

Mount the new drive (e.g. 'mount /dev/sdb1 /mnt') and copy over your current /home/user to /mnt/user.
Then add a new line to /etc/fstab for the new drive (the will be something like ' /dev/sdb1 /home ext3 relatime 0 2', assuming its an ext3 filesystem, and sdb1 is the new drive).
When you reboot, you'll need to change the permissions of your new home directory so that your user owns them.  As root, do:

chown -R USER /home/USER
chgrp -R GROUP /home/USER

(Your primary group is probably the same as your username).

Your old /home/USER folder will still be there on the first drive, but not visible in the file system.  If you need to free up this space, you could mount the drive from a live CD and delete it.

Best of luck.

Fishonadish

Just use `cp -Rp <src> <target>`, really. The p-switch ensures preservation of permissions, ownerships, and timestamps.

---

