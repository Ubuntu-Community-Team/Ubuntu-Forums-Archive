---
title: "change mount point for auto mount USB HDD"
date: 2008-12-08
forum: Desktop Environments
---

### Post by _sebastian_ on 2008-12-08
Hi all,

I got myself a external HDD. I created a ext3 partition and added a label for the new partition. So far all works.

the drive is always mounted to /media/%LABELNAME%

Now I wanted to have the mount point in a different directory. 
I had a look at the "Preferences" of the auto mounted drive there is a Drive and a Volume tab. They both seem to do the same or similar things.

[[IMG]http://img361.imageshack.us/img361/5467/screenshotlegendpropertgp9.th.png[/IMG]](http://img361.imageshack.us/my.php?image=screenshotlegendpropertgp9.png)

I added a new mount point to the "Mount Point" option in the setting section in the hope that this would do the trick.

After unmounting and re-plugging of the external HDD I got this error message and the partition was not mounted automatically anymore.

[[IMG]http://img214.imageshack.us/img214/5584/mounterrorsf7.th.png[/IMG]](http://img214.imageshack.us/my.php?image=mounterrorsf7.png)

So now I have two questions:
[LIST]
[*]**How can I undo what I did?**
[*]**How is this feature to be used correctly?**
[/LIST]

I had a search but could not come up with helping results, e.g. [this at help.ubuntu.com]("https://help.ubuntu.com/community/MoveMountpointHowto")

---

### Post by Kobalt on 2008-12-08
What exactly did you enter as a mount point (your syntax seems to be incorrect, it should be somthing like this : /disks/myusbdrive )? 
Did you create the mount point before trying to mount your drive?

---

### Post by _sebastian_ on 2008-12-08
Well I think I entered 
```
/data/e/
```
with the last **/**

where would I be able to check this?

---

### Post by Kobalt on 2008-12-08
Your syntax is correct then, but did you create this mount point before entering this? If not, you should do it this way : ```
sudo mkdir /data/e
```

---

### Post by _sebastian_ on 2008-12-08
Yes the folder exists, I am the owner...

---

### Post by Kobalt on 2008-12-08
What happens when you try to manually mount this drive to its mount point using the Terminal? ```
sudo mount /dev/sd*xx* /data/e
```

---

### Post by ajgreeny on 2008-12-08
You said you made an ext3 partition, but the first image attached shows just a fat16 partition.  Could that be part of your problem?

---

### Post by _sebastian_ on 2008-12-08
> **ajgreeny said:**
> You said you made an ext3 partition, but the first image attached shows just a fat16 partition.  Could that be part of your problem?

Hi ajgreeny,
the attached picture is from one of my USB sticks ... as the HDD does not show anymore.

AND

mounting works: ```
/dev/sdc2 on /daten/e type ext3 (rw)
```

---

### Post by _sebastian_ on 2008-12-10
bump,

Can anyone tell me where these settings are saved? :confused:
(talking about the mount point change in the external drive preference)

EDIT: I found this post [http://ubuntuforums.org/showthread.php?t=147536](http://ubuntuforums.org/showthread.php?t=147536) but I still don't know where the changed setting is saved

---

### Post by _sebastian_ on 2008-12-10
I found the location where the setting is saved...

using the gconf-editor I went to system/storage and there was a entry with the harddrive info.

I deleted the mount value/key.

After a while when I unplugged it the automount worked again.

---

### Post by Azyl on 2008-12-12
can you please send me a private mesage with the location of that file were the value was stored pls

---

### Post by _sebastian_ on 2008-12-12
...
mmaybe I was not clear. Yes I found the location where this new mount name is saved, BUT it is not saved in a file. At least I did not find one.
but when you type gconf-editor in you command line/terminal the gnome configuration editor will open and there you can find it at the location described in the post.

---

