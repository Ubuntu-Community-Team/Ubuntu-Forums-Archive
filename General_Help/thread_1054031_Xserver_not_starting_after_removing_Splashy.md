---
title: "Xserver not starting after removing Splashy"
date: 2009-01-29
forum: General Help
---

### Post by bineeshm on 2009-01-29
Hi!
I tried Splashy yesterday following methods mentioned in the following site:
[http://www.makeuseof.com/tag/how-to-easily-change-your-usplash-screen-in-ubuntu/](http://www.makeuseof.com/tag/how-to-easily-change-your-usplash-screen-in-ubuntu/)

I didnt like it much, so removed Splashy and re-installed Usplash again. 

Now, the system is not able to connect to Xserver and GDM is not coming up. I tried reconfiguring Xserver by,

sudo dpkg-reconfigure xserver-xorg

didnt help.

similarly gdm or startx couldnt do anything at all. 

I think the Splashy wasnt removed properly (didnt use Purge). Could this be an issue?? Can someone assist in getting this fixed??

Thanks much in advance for the help.

Cheers,

---

### Post by redilyn on 2009-01-29
I'm guessing you followed the two steps they describe for changing back to usplash?

```

sudo apt-get autoremove splashy splashy-themes
sudo apt-get install usplash

```

If you want to try a purge just incase run the following

```

sudo apt-get purge splashy splashy-themes

```

---

### Post by bineeshm on 2009-01-29
Thanks,

But would this fix the issue i.e. unable to start Xserver??

---

### Post by redilyn on 2009-01-29
I don't know.

So is the problem can not connect to xserver or can not start xserver?

---

### Post by bineeshm on 2009-01-29
The problem is not able to connect to Xserver, as a reason startx isnt helping. After boot loader i get a message like,

Kinit: no resume image, doing normal boot.

Also, i'm not able to use apt-get or anyother file operation as system seem to have locked all files/folders for writing :(

---

### Post by redilyn on 2009-01-29
Can you boot into recover mode and choose the option to fix X server?

---

### Post by bineeshm on 2009-01-29
Tried it too... not of any help :(

---

### Post by redilyn on 2009-01-29
Can you boot to recover mode, choose drop to root prompt.

Then try startx again and post the output here please.

---

### Post by bineeshm on 2009-01-29
Alright. Did so and here is what I got after lots of messages that I wasnt able to catch,

Code:
X: Warning; Process set to priority -1 instead of requested priority 0
Fatal Server error: could not create lock file in /tmp/.tX0-lock
Giving up
xinit: No such file or directory (error 2): unable to connect to X Server
xinit: No such process (error 3): Server error
xauth: error in locking authority file /root/.X authority

---

### Post by redilyn on 2009-01-29
Did you run any chmod command?

Can you run the following and post the output

```

sudo ls -l /tmp

```

---

### Post by bineeshm on 2009-01-29
Alright, it displayed lots of files and folders... all but one in 500 permission (drw---------)
The only other directory is hsperfdata_bineesh

Does it tell anyting?? I'm really thinking of formatting and re-installing as I need to do some work in another 5 hours :(

---

### Post by redilyn on 2009-01-29
Ya thats not right....

Try this

```

sudo chmod 1777 /tmp

```

Then try startx again and post the output if it fails.

---

### Post by bineeshm on 2009-01-29
1777 or should it be 777???

And after doing that, i assume that i need to restart the system normally right??

---

### Post by redilyn on 2009-01-29
Nope do 1777

Also you shouldnt have to reboot, just try startx again

The 1 means sticky bit which as far as i know means = do not let anyone delete or change permissions on this folder.

---

### Post by bineeshm on 2009-01-29
alright, here i goooo.....

---

### Post by bineeshm on 2009-01-29
No help... here is what I got:

Chmod: Changing permissions of '/tmp' : Read-only file system

Permissions wasnt changed at all

---

### Post by redilyn on 2009-01-29
Alright, I was wondering if that might be the problem.

try an fsck where /dev/sdX is your partition letter and number ie /dev/sda1

```

fsck /dev/sdX

```

---

### Post by bineeshm on 2009-01-29
Trust I did that previously when I started my system in Recovery mode... is there any other step I need to perform after doing fsck???

---

### Post by redilyn on 2009-01-29
No I don't think you did but it is strange. The file system should only be mounted read only in case of an error.

Hopefully fsck will find and correct the problem.

You didn't make any changes to fstab did you??

Wait..... part of those directions you followed told you to edit fstab and enter vga=791 right.

I bet thats your problem.

I think you are going to need your livecd for the next part, do you have one handy?

See next post for directions

---

### Post by bineeshm on 2009-01-29
yep... I'm postig these messages via Live CD... I have only this system at home and I reboot for every step you are telling :)

And about fstab, I dont know what it is... I'm no techie and dont try those stuff... 

As you have pointed, I did VGA=791 previously, i checked it now and it doesnt exist anymore

---

### Post by bineeshm on 2009-01-29
Should I do fsck first or shall we go on with the Live Cd??

---

### Post by redilyn on 2009-01-29
Okay :)

While inside the livecd try to mount the problem drive. Simplest way is to just look for it under places and see if it will open.

If it will do the following

```

sudo gedit /media/disk-1/boot/grub/menu.lst - [COLOR="Red"]might be /media/disk[/COLOR]

```

Look for the entry where you added vga=791 and remove the vga=791 part.

Then try to reboot again.

If you can not mount the drive by opening it in places you may need to mount it from the command line.

I will post those steps if we get to that point :)

---

### Post by redilyn on 2009-01-29
> **bineeshm said:**
> Should I do fsck first or shall we go on with the Live Cd??

Follow the steps to edit your menu.lst. we are going to forget fsck for now since i dont think it will fix your problem

---

### Post by bineeshm on 2009-01-29
Yep, here is how the menu.lst looks:

```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3ab151b1-4c5f-4d7a-bbcf-04fbee756305 ro quiet splash
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3ab151b1-4c5f-4d7a-bbcf-04fbee756305 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=3ab151b1-4c5f-4d7a-bbcf-04fbee756305 ro quiet splash
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=3ab151b1-4c5f-4d7a-bbcf-04fbee756305 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3ab151b1-4c5f-4d7a-bbcf-04fbee756305 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3ab151b1-4c5f-4d7a-bbcf-04fbee756305 ro  single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

Looks any good???

---

### Post by redilyn on 2009-01-29
Yep, if that is the correct menu.lst (not the livecd menu.lst) then you should be good to go....

Give it a try and see what happens.

Honestly if this doesn't work then the only other thing I can think to try is an fsck on the drive.

Also you could try to boot an older kernel but it most likely will not work.

---

### Post by redilyn on 2009-01-29
Taurus - If you have been reading this thread can you make a suggestion on what to do next??

---

### Post by bineeshm on 2009-01-29
Actually, this is how the menu.lst is all the while. I tried the older kernel too, but no luck.
Let me try fsck once more and check startx... will fall back soon with the results.

Really appreciate your help...

---

### Post by redilyn on 2009-01-29
Your very welcome. Wish I could be more help.

Last command I would think you might try would be

```

sudo update-initramfs -u

```

But that should have been run when you reinstalled usplash. If it wasn't its probably to late now since you have a read only file system. If all else fails you might want to try it just to see if it will work.

---

### Post by bineeshm on 2009-01-29
yep... all else have failed, should i restart and run it at Recovery Mode - Root prompt??

---

### Post by bineeshm on 2009-01-29
and if it doesnt work, should i reinstall OS once more??

---

### Post by redilyn on 2009-01-29
Yep run it from recovery root prompt.

Ya, I hate to say it (plus I don't think we are supposed too) but it that doesn't work its either wait for someone who knows more about the problem then me or reinstall ubuntu....

If you reinstall, and havn't done so previously. Be sure to create a seperate partition for /home

That way if you ever have to reinstall again your personel files and settings will be saved.

---

### Post by bineeshm on 2009-01-29
ok... that shouldn't be a proble. Since screwing up systems is very natural for me, I take backups very often... Its really pain to install the system once again is the trouble :(
. anyways, I'll run the last command once more and give a try...

---

### Post by bineeshm on 2009-01-29
didnt help :(
Trust I better reinstall the OS... Thanks much for the help...

---

### Post by redilyn on 2009-01-29
You really should setup a separate /home partition for just that reason.

I'm known for breaking my system as well, having a separate /home allows me to reinstall ubuntu without losing all my system and application settings plus all my data files.

With a setup including the separate /home a reinstall only takes about 40min for the install, update, and install of various applications.

I wish you luck, sorry I couldn't help you resolve your problem.

---

### Post by bineeshm on 2009-01-29
Thats ok.
BTW, Ubuntu by default creates all in one partition (other than swap).. how should i create a seperate partition for home. Trust that would be much helpful even for future (i dont expect this will be the last time I'm gonna end up like this :) )

---

### Post by redilyn on 2009-01-29
Ok, when you get to the partitioning section of the install choose custom.

Delete your existing ubuntu partition

You will want to create 3 partitions as follows

10-15GB ext3 mount point /
1-2GB swap
*GB ext3 mount point /home

I say *GB cause I don't know what size hard drive you have.

I know that might not sound very clear, but when you get to that section and look at the options you will be able to figure it out :)

---

### Post by bineeshm on 2009-01-29
Alright, will do so... thanks very much...
Have a great day ahead!!!

---

### Post by redilyn on 2009-01-29
Oh, on a side note since were talking about it.

After you have your separate /home, if you have to reinstall again you do the same custom step as above but instead of deleting the home partition you just:

Choose the /home partition (be sure to remeber the size!) -> Then edit -> use as ext3 -> Mount point /home

---

### Post by bubba_169 on 2009-05-05
Its probably not of much help now but Ill post anyway incase anyone has the same problem. I got around this problem recently on jaunty by booting into a live cd, chroot onto my old root drive and then reinstalling lsb-base through apt.

Removing splashy removes an essential config file that is put back in place when you reinstall lsb-base. Hope this can help someone...

---

