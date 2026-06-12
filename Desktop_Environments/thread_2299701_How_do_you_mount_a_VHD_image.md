---
title: "How do you mount a VHD image"
date: 2015-10-20
forum: Desktop Environments
---

### Post by mattig89ch on 2015-10-20
Hidy ho all,  I managed to get a bit of malware my Mcafee subscription couldn't get rid of.  Quite frankly, I tried everything you could think of, and a bit more besides.  It was a lovely piece of malware that opened 20 web pages, each with audio saying something like "This is the blue screen of death.  This means you computer has a virus.  Call the following number to remove this virus."  And when you call the number, they ask for a thousand dollars to remove the message.  I just threw up my hands in frustration, and created a VHD image of my windows install.  Then installed Ubuntu LTS 14.0.4 x64.  Now, I wanted to work on getting my files off that vhd image of my hard drive, and putting them in my shiny new Ubuntu install.  So, how does one go about mounting a VHD image of a hard drive within Ubuntu?

---

### Post by yancek on 2015-10-20
The link below has a basic explanation and if you do an online search, you will find a lot of other sites with more detailed information.

[http://askubuntu.com/questions/202571/how-to-mount-a-virtual-hard-disk](http://askubuntu.com/questions/202571/how-to-mount-a-virtual-hard-disk)

---

### Post by QDR06VV9 on 2015-10-20
This might be a little easier to follow.
[http://bethesignal.org/blog/2011/01/05/how-to-mount-virtualbox-vdi-image/](http://bethesignal.org/blog/2011/01/05/how-to-mount-virtualbox-vdi-image/)

---

### Post by mattig89ch on 2015-10-20
Thanks for the help all,

Both those links are quite a bit confusing to me.

yancek, your link mentions a mount point.  But I didn't see what a mountpoint was in that post.  Is that a drive letter, or something else?

runrickus, your post was easier to follow.  But it made some assumptions on knowing how to do things.  For example, it says to install the qemu tools.  But it doesn't say how to install them, or where to find them to install them.  That's just an example, but the article is filled with assumptions like that.

Now, I'm not looking for someone to just type out the commands and paste them into here.  But I do need some explanations for a true linux novice

---

### Post by QDR06VV9 on 2015-10-21
> **mattig89ch said:**
> Thanks for the help all,

Both those links are quite a bit confusing to me.

yancek, your link mentions a mount point.  But I didn't see what a mountpoint was in that post.  Is that a drive letter, or something else?

runrickus, your post was easier to follow.  But it made some assumptions on knowing how to do things.  For example, it says to install the qemu tools.  But it doesn't say how to install them, or where to find them to install them.  That's just an example, but the article is filled with assumptions like that.

Now, I'm not looking for someone to just type out the commands and paste them into here.  But I do need some explanations for a true linux novice

Sorry about that simply install qemu-utils
```
sudo apt-get install qemu-utils
```


Now it says to
Load the nbd kernel module. Yes, I&#8217;m serious, the network block device module! (Note: All of the following commands require superuser permissions, so escalate your privileges in whatever way makes you most comfortable.)
So that is done by
**Edited 10-23-2015 Updated Code**
```
[COLOR=#111111][FONT=Consolas]sudo rmmod nbd
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]sudo modprobe nbd max_part=16[/FONT][/COLOR]
```


Then run qemu-nbd, which is a user space loopback block device server for QEMU-supported disk images. Basically, it knows all about weird disk image formats, and presents them to the kernel via nbd, and ultimately to the rest of the system as if they were a normal disk.


```
qemu-nbd -c /dev/nbd0 <vdi-file>
```
Of course you will need to replace <vdi-file> with your vdi name.


Then That command will expose the entire image as a block device named /dev/nbd0, and the partitions within it as subdevices. For example, the first partition in the image will appear as **/dev/nbd0p1.**


Now you could, for instance, run cfdisk on the block device, but **you will most likely want to mount an individual partition**.


```
mount /dev/nbd0p1 /mnt
```
Again changing if needed.


Now you should be able to move things in and out as he states.
And in his own words
> Gadzooks! Now you can muck around inside the filesystem to your heart&#8217;s content. Go ahead and copy stuff in or out, or if you&#8217;re feeling fruity, have some chrooty: chroot /mnt.


And when you&#8217;re done, unmount the filesystem and shut down the qemu-nbd service.


By way of
```
umount /mnt
qemu-nbd -d /dev/nbd0
```



Hope that is clear enough.
Best Regards

---

### Post by mattig89ch on 2015-10-21
Wow, thats actually very helpful.  Thanks for that!

Belive it or not, I had slept on it and gave it a bit of thought, and was going to try creating those commands myself.  though it looks like I would have been off on every command, I think I would have been close.

I'll give those a try and post back here success or failure

---

### Post by marcus_s on 2015-10-24
You can use [FONT=courier new]qemu-nbd[/FONT] for these purposes.

This tool is part of the qemu package (a super-cool virtual machine tool). You can install it with [FONT=courier new]sudo apt-get install qemu[/FONT] (large package). Once you have it, [FONT=courier new]qemu-nbd[/FONT] will be installed for you. This is a small nifty tool that allows you to mount VHD images.

You can then mount the image with:

[FONT=courier new]sudo modprobe nbd max_part=16
sudo qemu-nbd -c /dev/nbd0 [COLOR=#ff0000]/path/to/vhdfile[/COLOR]
sudo partprobe /dev/nbd0
sudo mount /dev/nbd0p1 /mnt/image[/FONT]

Obviously you need to replace the path in red with the actual path to where the VHD image is located. Don't forget to unmount the image like you would as normal after you're done.

[FONT=courier new]sudo umount /mnt/image
[/FONT]
Hope that helps.

---

### Post by mattig89ch on 2015-10-25
my apologies for not posting back sooner.  I simply haven't had the free time to try mounting the image, then go through and try cherry picking through the files.

---

