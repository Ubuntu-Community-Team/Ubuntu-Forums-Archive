---
title: "Something Quick..."
date: 2009-05-02
forum: General Help
---

### Post by The_Lost_World on 2009-05-02
Hey, a tiny but very important question here, please answer.

I see people calling the partitions "/home" and "/swap", but also calling the swap partition just "swap". How should I set them when partitioning? As "/example" or "example"?

Thank you!

---

### Post by Locutus_of_Borg on 2009-05-02
as "swap"

do not assign swap a mount point

---

### Post by soro2005 on 2009-05-02
/ is root, ground zero so to speak. /example is example as a child of root. /media/example is example as a child of media as a child of /. Your directory is never called /example, but example. If it's a child of /, that makes it /example. :guitar:
Plus, this is about the mount point (i.e., where within your directory structure your partition is added). It is not about creating or naming (labeling) of partitions.

---

### Post by jmszr on 2009-05-02
Locust_of_Borg & soro2005,

What if you have already set it up as "/swap"? How is the mount point removed and "swap" substituted?

---

### Post by The_Lost_World on 2009-05-02
> **Locutus_of_Borg said:**
> as "swap"

do not assign swap a mount point
Thank you very much!

---

### Post by soro2005 on 2009-05-02
> **jmszr said:**
> Locust_of_Borg & soro2005,

What if you have already set it up as "/swap"? How is the mount point removed and "swap" substituted?

If you mount it as /swap, then it will probably not be used as swap space. The point is that the swap space isn't mounted as part of the file structure accessible by users. You can see whether your system is currently using a swap space, and which disk partition is used for it, by entering
```
swapon -s
```
at a command prompt.

---

### Post by jmszr on 2009-05-02
soro2005, 

From these results: 
> jeff@jeff-desktop:~$ swapon -s
Filename				Type		Size	Used	Priority
jeff@jeff-desktop:~$ 



I would think that I don't have a swap. What should I do to rectify this? I do have a "/swap" (/dev/sda2) which obviously is wrong.

---

### Post by soro2005 on 2009-05-02
Please post the output of
```
cat /etc/fstab
```
If it's too much, or sensitive, only post
```
cat /etc/fstab | grep swap
```
Also post the output of
```
ls -al /swap
```
The last one is to have a look into the partition and make sure it is empty, for you might screw it over in one of the next steps. :-D

*Edit: Don't post the output of the last command, just make sure it returns nothing. If it does return something, secure the data that's in /swap *

*Edit again: Also post the output of
```
blkid /dev/sda2
```

---

### Post by jmszr on 2009-05-02
soro2005,

These are the outputs:

```
jeff@jeff-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dec6c8d7-254f-4714-8187-3f70c9309f11 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=afc7132f-6acf-4d1d-8b17-7b683c401373 /Wubi           ext3    relatime        0       2
# /dev/sda4
UUID=28878822-fc6c-49ce-9c86-27b0678e28eb /home           ext3    relatime        0       2
# /dev/sda2
UUID=4268c9ee-327c-4d7e-9379-748c8049dc34 /swap           ext3    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
jeff@jeff-desktop:~$ 


```


```
jeff@jeff-desktop:~$ ls -al /swap
total 24
drwxr-xr-x  3 root root  4096 2008-11-12 14:55 .
drwxr-xr-x 24 root root  4096 2009-01-09 18:37 ..
drwx------  2 root root 16384 2008-11-12 14:55 lost+found

```

```
jeff@jeff-desktop:~$ blkid /dev/sda2
jeff@jeff-desktop:~$ sudo blkid /dev/sda2
/dev/sda2: UUID="4268c9ee-327c-4d7e-9379-748c8049dc34" TYPE="ext3" 
jeff@jeff-desktop:~$ 

```

I hope that is what you need - I didn't see anything sensitive so I just posted the output.

Thank you.

Edit: "Wubi" is an empty partition.

---

### Post by Locutus_of_Borg on 2009-05-02
you cannot actually mount swap anyway, so anything mounted in your file system is not swap space.  

from your outputs above, to create a swap space:
```

umount /dev/sda2
mkswap /dev/sda2
swapon /dev/sda2
nano /etc/fstab
```
find the line right below "#/dev/sda2" and delete it, then in its place enter:
```
/dev/sda2 none swap defaults 0 0
```

now you will have swap space

---

### Post by jmszr on 2009-05-03
Locutus_of_Borg,

While I tried to delete the line under "#/dev/sda2" and thought I had - "/swap" no longer shows under System Monitor > File Systems, it still shows```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dec6c8d7-254f-4714-8187-3f70c9309f11 /               ext3    relatime,err$
# /dev/sda3
UUID=afc7132f-6acf-4d1d-8b17-7b683c401373 /Wubi           ext3    relatime    $
# /dev/sda4
UUID=28878822-fc6c-49ce-9c86-27b0678e28eb /home           ext3    relatime    $
# /dev/sda2
UUID=4268c9ee-327c-4d7e-9379-748c8049dc34 /swap           ext3    relatime    $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[CODE}
under[CODE]nano /etc/fstab
```

How do I delete that line, or can I comment it out and then add:```
/dev/sda2 none swap defaults 0 0
```

Your help is much appreciated.

---

### Post by soro2005 on 2009-05-03
Only superuser can edit the file, so you have to use sudo. Use gedit if you prefer
```
gksu gedit /etc/fstab
```
Do *not* delete the line # /dev/sda2. It is commented out, deleting it has no effect whatsoever, and the line that mounts /dev/sda2 is the following one anyway. Rather, cange the following line, which now ends in /swap ext3 relatime, to read
```
UUID=4268c9ee-327c-4d7e-9379-748c8049dc34 none swap sw 0 0
```
Save the file, then:
```
sudo umount /swap && sudo mkswap /dev/sda2 && sudo swapon -a
```
Then you can verify whether it has worked with swapon -s. Now reboot to see wether the change sticks. /swap should now be fully empty, without even lost+found. You can delete it with
```
sudo rm -r /swap
```

---

### Post by The_Lost_World on 2009-05-03
Hey, another thing from me...

I'm downloading and planning on installing the newly released Jaunty Jackalope. Will the installation GUI and methods differ from Intrepid Ibex in any way?

---

### Post by soro2005 on 2009-05-03
> **The_Lost_World said:**
> Hey, another thing from me...

I'm downloading and planning on installing the newly released Jaunty Jackalope. Will the installation GUI and methods differ from Intrepid Ibex in any way?

I guess not substantially, but I haven't installed it, just upgraded.

---

### Post by Rinzwind on 2009-05-03
> **The_Lost_World said:**
> Hey, another thing from me...

I'm downloading and planning on installing the newly released Jaunty Jackalope. Will the installation GUI and methods differ from Intrepid Ibex in any way?

Nope. Not in a logical sence anyways. It looks a bit different but it has exactly the same questions in the same order.

---

### Post by jmszr on 2009-05-03
soro2005,

   Everything looks good so far. The last (hopefully) question I have is how do I now establish a "swap" and its size?

Sincerely Much Appreciated.

---

### Post by soro2005 on 2009-05-03
> **jmszr said:**
> soro2005,

   Everything looks good so far. The last (hopefully) question I have is how do I now establish a "swap" and its size?

Sincerely Much Appreciated.

The swap space will be the size of the partition you have now declared to be swap. It should be in use if you have changed fstab and then issued swapon -a. You can verify that with
```
swapon -s
```
If you want to change the size, you will have to use a partition manager to resize partitions. That's a bitch if you don't have a lot of spare space on your drive. Depending on how much memory you have, you won't need a lot of swap anyway. I have 3 GB memory, and the only time my machine has ever used the swap space was b/c of memory leaks. If you want to hibernate, you need a swap space that's a little larger than your RAM, though.

---

### Post by jmszr on 2009-05-03
soro2005,

          I changed fstab:
```
jeff@jeff-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dec6c8d7-254f-4714-8187-3f70c9309f11 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=afc7132f-6acf-4d1d-8b17-7b683c401373 /Wubi           ext3    relatime        0       2
# /dev/sda4
UUID=28878822-fc6c-49ce-9c86-27b0678e28eb /home           ext3    relatime        0       2
# /dev/sda2
 UUID=4268c9ee-327c-4d7e-9379-748c8049dc34 none swap sw 0 0   
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
jeff@jeff-desktop:~$ 

```

swapon -a gives this:

```
jeff@jeff-desktop:~$ swapon -a
swapon: cannot canonicalize /dev/disk/by-uuid/4268c9ee-327c-4d7e-9379-748c8049dc34: No such file or directory
swapon: cannot stat /dev/disk/by-uuid/4268c9ee-327c-4d7e-9379-748c8049dc34: No such file or directory

```

Then swapon -s outputs:
```
jeff@jeff-desktop:~$ swapon -s
Filename				Type		Size	Used	Priority
jeff@jeff-desktop:~$ 

```

I have 2GB RAM but occasionally it fills up, wouldn't mind having some "swap" space. I am not sure of what you mean by "the size of the partition you have now declared as swap".

Thanks.

Edit: Or should I go with a swap file?

---

### Post by soro2005 on 2009-05-03
Sorry, that must have been b/c swap vs ext3 changes the uuid. In fstab (gksu gedit /etc/fstab), Either replace UUID=4268c9ee-327c-4d7e-9379-748c8049dc34 with /dev/sda2 to read
```
/dev/sda2 none swap sw 0 0
```
or find out the correct UUID with
```
blkid /dev/sda2
```
and copy the long hex number to substitute what now is 4268c9ee-327c-4d7e-9379-748c8049dc34. Then:
```
sudo swapon -a
```
"The size of the partition now declared as swap" would be /dev/sda2

---

### Post by jmszr on 2009-05-03
soro2005,

         I went with the second option and everything is good. 

                                              Thank You,

                                                            Jeff

---

### Post by cariboo on 2009-05-03
Thank you soro2005, I didn't set up the swap partiton properly on my server. Your instructions solved my problem.

---

### Post by The_Lost_World on 2009-05-03
> **Rinzwind said:**
> Nope. Not in a logical sence anyways. It looks a bit different but it has exactly the same questions in the same order.
That's good to know, thanks!

---

