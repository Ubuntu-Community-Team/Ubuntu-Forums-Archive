---
title: "Hibernate no longer works (Intrepid)"
date: 2009-02-04
forum: General Help
---

### Post by cometa2k7 on 2009-02-04
I'm currently running Intrepid Ibex on my laptop. Hibernate used to work fine, but now it just flickers the screen once or twice, locks it, then does nothing. My laptop power light flashes as it does when beginning hibernation.

I have not updated my kernel recently - not since I last successfully used hibernation.

---

### Post by cometa2k7 on 2009-02-04
Ok, I have located a possible source of the error - my swap isn't mounted.

How do I get Ubuntu to use the swap space? I can do swapon in GParted, but get an error when using ```
sudo swapon -a
```

The error is ```
swapon: cannot stat /dev/disk/by-uuid/7e506e89-5856-4b2f-b727-db92c5408ecf: No such file or directory

```

---

### Post by cometa2k7 on 2009-02-05
I fixed it :D

For anyone else who encounters this, this was my solution:

```
sudo swapon -a
```

That returned an error with the correct UUID in it, that's necessary later.

```
sudo mkswap -U UUID /dev/sdaX
```

Replace the 'X' with your drive number (you can check this in GParted which is the partition editor in Ubuntu.

Replace the 'UUID' with whatever UUID was returned after the first command - it should look something like '7e506e89-5856-4b2f-b727-db92c5408ecf'

Please note that it may be necessary to first format the swap drive as something else (ie. ext2).

Now you just need to:
```
sudo swapon -a
```

Your swap should now work just as it did before it went wrong.

---

### Post by warped0ne on 2009-02-14
I tried this on my EeePC and was first told that my primary swap partition wasn't big enough.  So, I resized my primary drive and set the swap partition up on the secondary drive.

I then did exactly what is said above (except I used ***sdbX*** instead of ***sdaX*** for my drive, and I got the error:

**swapon: cannot stat /dev/disk/by-uuid/UUID: No such file or directory**

Is it possible to do this with the swap setup on a secondary drive?

---

### Post by warped0ne on 2009-02-14
I just tried this:

- Ran **ls -l /dev/disk/by-uuid/** to find the other drives UUID.
- Then **sudo mkswap -U UUID /dev/*sdbX*** to set the swap.
- Finally **sudo swapon -a**

Then I exited the Terminal and tried to enter Hibernation.  The Eee went to a blank screen with a flashing cursor for about 60 seconds, then the screen went blank.  My first thought was "Success!" but I was disappointed to see that it went through a complete boot up (POST and all) after I pressed the power button.

I'm lost at this point.  Help would be very much appreciated.

---

### Post by cometa2k7 on 2009-02-15
Did you try formatting the swap drive to something else first? When I was sorting this, it wouldn't actually have any effect until I'd formatted the drive to something else first.

So I would suggest opening GParted, or another partition editor, then format your swap drive to somethign else other than linux-swap. I used ext2 and that seemed to work, but it'd probably work with anything else. One you've done that, simply open a terminal and mkswap it.

I hope this helps.

---

### Post by warped0ne on 2009-02-17
Actually, I had to delete my swap partition because my computer kept booting saying that it could not load /dev/sdb5 (my swap-partition).  I couldn't get into the OS at all without running a Live SD card install and using gparted to fix the partition.  I could then boot into Ubuntu, but when I restarted again, it would do the same thing.  So, I deleted the swap-partition and resized the 2nd drive to the full 16GB.  It booted into the OS again, and I haven't tried restarting yet. 

If I get the same error after this, I'm going to reinstall and try to set up my swap-partitions differently.

---

### Post by lvleph on 2009-02-17
I did the above, and I am getting
```

sudo swapon -a
swapon: cannot stat /dev/disk/by-uuid/4fb0271b-1f9a-45fc-9b8c-1104d691b358: No such file or directory

```
I then used
```

ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2009-02-17 11:04 284F243607E75E6A -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-02-17 11:04 372f16b2-4c28-4d27-b75f-4b554acc73f5 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-02-17 16:31 373cce44-be72-43b0-b98e-0b8c5ba0f35a -> ../../sda4
lrwxrwxrwx 1 root root 10 2009-02-17 11:04 D200E77700E760C9 -> ../../sda1

```
Notice the UUID is different for sda4, so I then used
```
sudo mkswap -U 373cce44-be72-43b0-b98e-0b8c5ba0f35a /dev/sda4
Setting up swapspace version 1, size = 1052252 KiB
no label, UUID=373cce44-be72-43b0-b98e-0b8c5ba0f35a
```
With the exact same results.

---

### Post by lvleph on 2009-02-18
I just got my swap to turn on. From a different thread.
[quote=cdtech]You need to reconfigure your "/etc/fstab" file so it recognizes the location of the swap partition.
```

# /dev/sda5
UUID=f33563e3-48bc-4ec9-9b8c-a4783ed4109a none swap  sw     0       0
```

Use your own /dev or UUID:
```


blkid
```

and
```

sudo fdisk -l
```

Then just issue the command:
```

swapon -a
```

[/quote]
The problem stemmed from the wrong UUID in fstab.

---

### Post by qrwe on 2009-02-20
My problem is this: as the hard drives on EeePC with flash drives ain't very long lived, I got the advice to not make any swap partition at all as this will make the drives "grow old faster". It works all fine ..all but the hibernation option, as it somehow uses the swap partition.

Concluded question: Is it possible to use Hibernate without swap partitions?

---

### Post by lvleph on 2009-02-20
Look into [this](http://www.ubuntu-eee.com/wiki/index.php5?title=Fix:_hibernate).

I still have not been able to fix hibernate. Can anyone give me some more suggestions.

---

### Post by cometa2k7 on 2009-02-21
Ok, assuming that the UUID below is correct, which I think it should be, this should work.

Just open a terminal and run each command below in sequence.

```
sudo mkfs.ext2 -I /dev/sda4
```

```
sudo mkswap -U 4fb0271b-1f9a-45fc-9b8c-1104d691b358 /dev/sda4
```

```
sudo swapon -a
```

Then attempt to hibernate again. I don't know whether you were using the correct UUID, but I would advise you to use the one in this post.

---

### Post by lvleph on 2009-02-21
The result of the first command gave me this.
```

mkfs.ext2: invalid inode size - /dev/sda4
```

---

### Post by cometa2k7 on 2009-02-22
> **lvleph said:**
> The result of the first command gave me this.
```

mkfs.ext2: invalid inode size - /dev/sda4
```

I wasn't too sure about that command, so just format it to ext2 in GParted or another partition editor. After that, do the last two commands.

---

### Post by lvleph on 2009-02-22
I had to change my swap to that UUID in fstab, but I swapon: > cannot stat /dev/disk/by-uuid/4fb0271b-1f9a-45fc-9b8c-1104d691b358: No such file or directory
still get this error on sudo swapon -a.


EDIT: Ok, got swapon working. Not sure what I did, but it is working. Now I have the problem of going to hibernate and it just sits at a black screen with a cursor blinking; I press ctrl+alt+f1 and it goes to a logon in terminal, but I cannot type anything. I end up hard restarting. One time in the process of doing this I received
> 
CIFS VFS: No response for CMD 50 mid 36505
CIFS VFS: No response for CMD 50 mid 36507
CIFS VFS: No response for CMD 50 mid 36509
CIFS VFS: No response for CMD 50 mid 36511
CIFS VFS: No response for CMD 50 mid 36510
CIFS VFS: No response for CMD 50 mid 36506
CIFS VFS: No response for CMD 50 mid 36508
CIFS VFS: No response for CMD 50 mid 36512
CIFS VFS: Unexpected look up error -112
I have had a similar error on shutdown before too.

EDIT: I used [this](http://ubuntuforums.org/showthread.php?t=293513) to fix the CIFS error. However, I cannot seem to hibernate still.

EDIT: I tried to go back through the steps again. Formatted /dev/sda4 to ext2 then 
```
sudo mkswap -U 4fb0271b-1f9a-45fc-9b8c-1104d691b358 /dev/sda4
Setting up swapspace version 1, size = 2104508 KiB
no label, UUID=4fb0271b-1f9a-45fc-9b8c-1104d691b358
``````

sudo swapon -a
swapon: cannot stat /dev/disk/by-uuid/4fb0271b-1f9a-45fc-9b8c-1104d691b358: No such file or directory
``````

ls /dev/disk/by-uuid/
284F243607E75E6A                      3d0fb2b0-02fb-4e94-8a82-182471f706f3
372f16b2-4c28-4d27-b75f-4b554acc73f5  D200E77700E760C9

```
So the uuid I used does not exist.

---

### Post by cometa2k7 on 2009-02-23
As some sort of workaround, you could try turning the swap on in GParted. I can't remember whether this worked for hibernation when I did it, but it will turn the swap partition on.

Open GParted, right-click on your swap partition and click "Swapon"

---

### Post by lvleph on 2009-02-23
Yeah, I have done that and hybernation didn't work.

---

### Post by cometa2k7 on 2009-02-24
Well I'm all out of suggestions.

---

### Post by lvleph on 2009-02-24
I got the swap to finally turn on. I tried using s2disk and came up with some other issues. I started  thread on this issue, if you don't mind taking a look at it.
[http://ubuntuforums.org/showthread.php?t=1072642](http://ubuntuforums.org/showthread.php?t=1072642)

---

