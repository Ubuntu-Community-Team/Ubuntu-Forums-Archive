---
title: "0 bytes free, no docs., pics. etc. shortcuts?"
date: 2009-04-13
forum: General Help
---

### Post by Adavur on 2009-04-13
Hi

I've installed Ubuntu at my 4 gb USB-drive which works fine.

But today I got a strange bug. Suddenly I couldn't even save a simple text-file. I went to homefolder->right click->propeties->free space: 0 bytes!?

It is strange because I have space enough. My trash is empty, so I'm sure it's some kind of a bug.

I've tried it before, but the error disapeared again.

Is it a well known bug? Can somebody please help? I can't even post a screenshot for you, cause I can't save it...

Maybe it is useful to know that if I go to the menu Places the shortcuts for documents, pictures etc. is now gone.

Mathias (and sorry for my English :-S)

---

### Post by northern lights on 2009-04-13
Please open a terminal, run```
df
```and post the output here.

---

### Post by Adavur on 2009-04-13
Terminal

[HTML]Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540         0    252540   0% /lib/init/rw
varrun                  252540       104    252436   1% /var/run
varlock                 252540         0    252540   0% /var/lock
udev                    252540      2804    249736   2% /dev
tmpfs                   252540       104    252436   1% /dev/shm
rootfs                 3171880   3011156         0 100% /
/dev/sdb1              3948996   3937980     11016 100% /cdrom
/dev/loop0              691712    691712         0 100% /rofs
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
df: `/media/C-drev': No such file or directory
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                  3171880   3011156         0 100% /lib/modules/2.6.27-11-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
df: `/media/disk': No such file or directory
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
df: `/media/OneTouch4': No such file or directory
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
gvfs-fuse-daemon       3171880   3011156         0 100% /home/ubuntu/.gvfs
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
df: `/media/OneTouch4': No such file or directory
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
/dev/fuse              3171880   3011156         0 100% /home/ubuntu/.gvfs
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                     1024        16      1008   2% /tmp
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
overflow                  1024        16      1008   2% /tmp
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
overflow                  1024        16      1008   2% /tmp
tmpfs                   252540      2000    250540   1% /lib/modules/2.6.27-7-generic/volatile
overflow                  1024        16      1008   2% /tmp
[/HTML]

---

### Post by northern lights on 2009-04-13
> **Adavur said:**
> rootfs                 3171880   3011156         0 100% /
Man, your root filesystem _is_ full. You've gotta delete/move some stuff outta /home.

---

### Post by Adavur on 2009-04-13
But why did the docs, pics. etc shortcuts disappear?

---

### Post by Adavur on 2009-04-13
But thank you anyway.

Now the shortcuts came up again :)

---

### Post by hariks0 on 2009-05-27
I also encountered the same problem after running 'remastersys' which created a folder named 'remstersys' in /home and caused the problem. The contents of the folder amounted to the capacity of my /home. I manually deleted the /home/remastersys [of course using sudo]. The free space immediately came up again.

---

### Post by akrivitz on 2010-06-20
Same problem here on an external usb drive. 

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            230582428  76249840 142619616  35% /
none                   2020436       368   2020068   1% /dev
none                   2024936       848   2024088   1% /dev/shm
none                   2024936       196   2024740   1% /var/run
none                   2024936         0   2024936   0% /var/lock
none                   2024936         0   2024936   0% /lib/init/rw
/dev/sdc1            976521568 406771680 569749888  42% /media/MUSIC
/dev/sdb5            488375968 488375968         0 100% /media/MoviesTV

```


Check /dev/sbd5/  (/media/MoviesTV).... how am I using 488375968 bytes with 0 available? I can read from the drive fine as of now, but I can't write to it.... says there's no space left. However if I right click in nautilus and do properties, it says there is 240 gb of data on the drive. It's a 500gb so it should only be about half full..



any thoughts on how to restore write-access?

---

