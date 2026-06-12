---
title: "Mounting Folders?"
date: 2011-05-19
forum: Desktop Environments
---

### Post by DevilSolution on 2011-05-19
Hi guys and girls, ladies and gentleman. I have an issue with a new harddrive ive just installed, infact its not an issue just a general question that was to specific to search on google or find an answer on the forums.
Okay so basically i installed a new slave and gave myself permissions etc but my issue is that really what i need the slave to do is be the home of a few of my folders such as the var/cache/apt aswell as my /home/usernamex/certainfolders.

So im wondering if i can move/bind/mount my files into my new new hard drive so that i can save my small amount of space on my master for updates

i can use the terminal and preferably would like to use it.

thanks in advance guys

---

### Post by Nerotriple6 on 2011-05-19
Hello.

I have a text file that I use whenever I have to reinstall my OS. It is originally written to mount a Home folder but I think it will work for you as well.

Best of luck.:)

```
Move /home to it’s own partition


Having the “/home” directory tree on it’s own partition has several advantages, the biggest perhaps being that you can reinstall the OS (or even a different distro of Linux) without losing all your data. You can do this by keeping the /home partition unchanged and reinstalling the OS which goes in the “/” (root) directory, which can be on a seperate partition.

But you, like me, did not know this when you first installed Ubuntu, and have not created a new partition for “/home” when you first installed Ubuntu. Despair not, it is really simple to move “/home” to its own partition.

First, create a partition of sufficient size for your “/home” directory. You may have to use that new hard drive, or adjust/resize the existing partition on your current hard-drive to do this. Let me skip those details.

Next, mount the new partition:


$mkdir /mnt/newhome
$sudo mount -t ext3 /dev/hda5 /mnt/newhome


(You have to change the “hda5&#8243; in the above to the correct partition label for the new partition. Also, the above assumes that the new partition you created is formatted as an ext3 partition. Change the “ext3&#8243; to whatever filesystem the drive is formatted to.)

Now, Copy files over:
Since the “/home” directory will have hardlinks, softlinks, files and nested directories, a regular copy (cp) may not do the job completely. Therefore, we use something we learn from the Debian archiving guide:


$cd /home/
$find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/


Make sure everything copied over correctly. You might have to do some tweaking and honing to make sure you get it all right, just in case.


Next, unmount the new partition:

$sudo umount /mnt/newhome

Make way for the new “home”
$sudo mv /home /old_home

Since we moved /home to /old_home, there is no longer a /home directory. So first we should recreate a new /home by:
sudo mkdir /home

Mount the new home:
$sudo mount /dev/hda5 /home
(Again, you have to change “hda5&#8243; to whatever the new partition’s label is.)

Cursorily verify that everything works right.

Now, you have to tell Ubuntu to mount your new home when you boot. Add a line to the “/etc/fstab” file that looks like the following:

/dev/hda5 /home ext3 nodev,nosuid 0 2

(Here, change the partition label “hda5&#8243; to the label of the new partition, and you may have to change “ext3&#8243; to whatever filesystem you chose for your new “home”)

Once all this is done, and everything works fine, you can delete the “/old_home” directory by using:

$sudo rm -r /old_home
```

---

### Post by Morbius1 on 2011-05-19
You could do all this with symbolic links I suppose but I like to use bind myself. And I like to do it by creating my own upstart job::

Let's say you have folders in a mounted partition at: /mnt/Slave and you want corresponding folders in /home/usernamex/ to "bind" to them:

(1) Create an upstart job named "bindmount.conf"
```
gksu gedit /etc/init/bindmount.conf
```(2) With content that looks something like this:
```
# Remount with bind
#
description "Bind Partitions to Selected Directories"

start on stopped mountall

script
mount --bind /mnt/Slave/Documents /home/usernamex/Documents
mount --bind /mnt/Slave/Pictures /home/usernamex/Pictures
end script
```If you want to try it out before committing to an upstart job just run the individual commands from a terminal and see if it does what your want:

To mount:
```
sudo mount --bind /mnt/Slave/Documents /home/usernamex/Documents
```To unmount:
```
sudo umount /home/usernamex/Documents
```

---

