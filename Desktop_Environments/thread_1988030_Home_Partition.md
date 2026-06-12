---
title: "Home Partition"
date: 2012-05-26
forum: Desktop Environments
---

### Post by CWM84 on 2012-05-26
Hi Guys,

I had to reformat today... as I went though the installer, I didnt check the box to make the 222 gig partition home.. For the fear of it eracing whats on it... I thought it did it automatically.

So now I have the 99 gig / installation

and 222 gig... partition... ( no label ) 

I need to make the 222 gig.. the home partition... How can I do that without reformatting?

Thanks,
Christopher

---

### Post by Peripheral Visionary on 2012-05-26
You must have huge, ginormous hard drive! ;)

I recommend three partitions:

"[COLOR=DarkOrange]**Linux Swap**[/COLOR]," which should be about 2X your computer's RAM. Unless you have gigabytes of RAM and probably would never need swap space.

"[COLOR=DarkOrange]**/**[/COLOR]" which is for the Xubuntu operating system. Mine is 20 gb in size - about 5 times what Xubuntu needs!

"[COLOR=DarkOrange]**/home**[/COLOR]" where your pictures, music, photos, e-mail settings, bookmarks, etc are all kept.

When you install Xubuntu you can partition the hard drive and format everything except '[COLOR=DarkOrange]**/home**[/COLOR]." UNCHECK the "format this partition" box when selecting it.

---

### Post by dave0109 on 2012-05-27
Just to clarify: your 222GB partition already has data on it, which you want to be mounted as your /home partition.  In which case, first you need to find out the UUID of the partition.  You can do this with:-
```

sudo blkid

```
It may be obvious to you which partition you need.  If not, try getting a list of your drives and partitions with:-
```

sudo fdisk -l

```
That might give an error if you have a GUID Partition Table, in which case run up gparted instead (you may need to get this from the repositories).  Within that, you'll see which partition is 222GB and therefore what the partition "name" is, something like /dev/sda3 (for example).  Then, from the blkid command, you can match 'sda3' with the right UUID.

Now you need to edit the file /etc/fstab.  You should probably back up the file first to be safe.  Add a new line that goes like:-
```

UUID=<Insert your UUID>  /home   ext4   defaults   0   2

```
This says: mount the partition identified by the UUID onto /home, that it is an ext4 partition, use the default set of options, don't bother backing up with 'dump' and check this partition after the root partition. 
Of course, make sure that 'ext4' matches what your partition type actually is, as listed by the blkid command.

After that, you should be able to change directory out of the /home area and then mount the partition.  Alternatively reboot.

If you've messed something up bad and it doesn't boot OK, you can boot from a LiveCD, mount the root partition then restore the original fstab file.

---

### Post by anaconda on 2012-05-27
funny.
Your system is now configured about exactly the same than mine.

Why would you like to change it?

I prefer having the sama partition having the whole ubuntu.. including both "/" and "/home"
Then I have a separate 2TB HDD as a data-storage drive. IT functions like home and it has all my data on it.

I like to keep the data storage somewhere else than home, because ubuntu puts a lot of crap in home. Dont want to mix all that with my data... . For example all the settings files, and browswr caches etc.
reinstalling is easy. Just copy anything I need from home to the data hdd and reinstall...

You also need some swap, but swap doesnt have to be a partition. swap-files are jus as fast and easier to make if you already partitioned your HDD and forgot to make it.

---

### Post by CWM84 on 2012-05-27
> **anaconda said:**
> funny.
Your system is now configured about exactly the same than mine.
 
Why would you like to change it?
 
I prefer having the sama partition having the whole ubuntu.. including both "/" and "/home"
Then I have a separate 2TB HDD as a data-storage drive. IT functions like home and it has all my data on it.
 
I like to keep the data storage somewhere else than home, because ubuntu puts a lot of crap in home. Dont want to mix all that with my data... . For example all the settings files, and browswr caches etc.
reinstalling is easy. Just copy anything I need from home to the data hdd and reinstall...
 
You also need some swap, but swap doesnt have to be a partition. swap-files are jus as fast and easier to make if you already partitioned your HDD and forgot to make it.
 
 
SO theres no way of making that 200 gig partition.. my HOME partition... I ment to set that up as seperate. :(
 
Thanks,
Christopher

---

### Post by CWM84 on 2012-05-27
> **dave0109 said:**
> Just to clarify: your 222GB partition already has data on it, which you want to be mounted as your /home partition.  In which case, first you need to find out the UUID of the partition.  You can do this with:-
```

sudo blkid

```
It may be obvious to you which partition you need.  If not, try getting a list of your drives and partitions with:-
```

sudo fdisk -l

```
That might give an error if you have a GUID Partition Table, in which case run up gparted instead (you may need to get this from the repositories).  Within that, you'll see which partition is 222GB and therefore what the partition "name" is, something like /dev/sda3 (for example).  Then, from the blkid command, you can match 'sda3' with the right UUID.

Now you need to edit the file /etc/fstab.  You should probably back up the file first to be safe.  Add a new line that goes like:-
```

UUID=<Insert your UUID>  /home   ext4   defaults   0   2

```
This says: mount the partition identified by the UUID onto /home, that it is an ext4 partition, use the default set of options, don't bother backing up with 'dump' and check this partition after the root partition. 
Of course, make sure that 'ext4' matches what your partition type actually is, as listed by the blkid command.

After that, you should be able to change directory out of the /home area and then mount the partition.  Alternatively reboot.

If you've messed something up bad and it doesn't boot OK, you can boot from a LiveCD, mount the root partition then restore the original fstab file.
 UUID="c79777ae-1c7c-4f31-a7fe-3e17e7cf9674"

Thats a little bit complicated for me..

Right now.. I cant save ANYTHING to that 222 gig partition.... Maybe I should leave them seperate.. But how do I make it to where I can save things on that 222 gig partition.. Right now if I try to save things to it.. I just get a THATS A NO NO MESSAGE...

---

### Post by CWM84 on 2012-05-27
Thats a little bit complicated for me..

Right now.. I cant save ANYTHING to that 222 gig partition.... Maybe I should leave them seperate.. But how do I make it to where I can save things on that 222 gig partition.. Right now if I try to save things to it.. I just get a THATS A NO NO MESSAGE... Denial Msg...

---

### Post by madverb on 2012-05-27
Edit /etc/fstab and add this line and then restart the computer.

```
UUID=c79777ae-1c7c-4f31-a7fe-3e17e7cf9674  /home   ext4   defaults   0   2
```

---

### Post by CWM84 on 2012-05-28
> **madverb said:**
> Edit /etc/fstab and add this line and then restart the computer.

```
UUID=c79777ae-1c7c-4f31-a7fe-3e17e7cf9674  /home   ext4   defaults   0   2
```


I cant write to the file...

When going to it and opening it..

but when I save to it it says I cant write to it.

---

### Post by CWM84 on 2012-05-28
> **anaconda said:**
> funny.
Your system is now configured about exactly the same than mine.

Why would you like to change it?

I prefer having the sama partition having the whole ubuntu.. including both "/" and "/home"
Then I have a separate 2TB HDD as a data-storage drive. IT functions like home and it has all my data on it.

I like to keep the data storage somewhere else than home, because ubuntu puts a lot of crap in home. Dont want to mix all that with my data... . For example all the settings files, and browswr caches etc.
reinstalling is easy. Just copy anything I need from home to the data hdd and reinstall...

You also need some swap, but swap doesnt have to be a partition. swap-files are jus as fast and easier to make if you already partitioned your HDD and forgot to make it.

it wont let me write to it.. thats why I was asking for help :( 
( THE 222 GIG partition )

---

### Post by kansasnoob on 2012-05-28
IMHO it would be best for you to just reinstall properly (without formatting /home), but first please post the output of:

```
sudo parted -l
```

And:

```
df -H
```

Please do so while booted into your freshly installed Xubuntu ....... NOT using a live CD!

EDIT: I just thought to ask what version of Xubuntu you're installing. You didn't say in your OP whether this is 12.04 or not. So please also include the output of:

```
lsb_release -a
```

---

### Post by dave0109 on 2012-05-28
> **CWM84 said:**
> I cant write to the file...

When going to it and opening it..

but when I save to it it says I cant write to it.

You need to edit the file with super-user priviledges...
```

sudo leafpad /etc/fstab

```

Or, if this level of tinkering is too much for you, then do as kansasnoob suggests.  Re-install and start again, this time taking care to re-use that 222GB partition as your /home.

---

### Post by CWM84 on 2012-05-28
> **CWM84 said:**
> it wont let me write to it.. thats why I was asking for help :( 
( THE 222 GIG partition )

Thank you... I reformatted....

---

