---
title: "Grub menu not displaying"
date: 2009-04-27
forum: General Help
---

### Post by thegr8brian on 2009-04-27
I just updated from 8.10 to 9.04 and I was able to boot a few times and now all the sudden when I turn on my computer the bios splash and then where it would normally display the grub boot menu I just get a black screen with the grub prompt that looks like

Grub>

So now I am currently operating from a USB drive running 9.04 live and I have tried reinstalling grub several times by doing...
```
sudo grub
```
```
root (hd0,4)
```
```
setup (hd0)
```


this made no difference however...how can I bring back my grub boot menu?

---

### Post by spiderbatdad on 2009-04-27
the method you used doesn't look all together right. Please see community documentation:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

    * Type the following and press enter:

      find /boot/grub/stage1

      If you get "Error 15: File not found", try the following:

      find /grub/stage1

      Using this information, set the root device (fill in X,Y with whatever the find command returned):

      grub> root (hdX,Y)

      Install Grub:

      grub> setup (hd0)

(In case you want to install GRUB to another drive (like hdX) use the above command as 'setup (hdX)' and then continue)

    * Exit Grub:

      grub> quit

---

### Post by thegr8brian on 2009-04-27
I've followed those instructions...

here is the result I get...
```
grub> root (hd0,4)
root (hd0,4)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,4)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

```

but when I reboot it still just sits at the grub prompt...

---

### Post by spiderbatdad on 2009-04-27
not sure what is happening. How about trying the super grub disk?

---

### Post by thegr8brian on 2009-04-27
What is the super grub disk and how do I use it?

---

### Post by spiderbatdad on 2009-04-27
there are instructions in the community docs I linked you to previously. Also google super grub disk will take you to the site.

---

### Post by thegr8brian on 2009-04-27
I tried using the disk but there was no luck...it was able to get windows to boot again, but it could not boot ubuntu there was something that read like error 15 something about fstab and mount point... so I looked up my fstab and here it is...
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8f4288fb-aa2c-4ad5-b0d7-888a6ef88578 /               ext4    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=af628ec4-1b07-4acd-9efe-81c74e97ba7c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

To me that looks fine but I dunno any ideas?

---

### Post by thegr8brian on 2009-04-27
I forgot to mention that it also said something about my stage1/stage2 being mismatched...

---

### Post by thegr8brian on 2009-04-27
Also now when the computer starts it just says loading grub stage1.5... and then it does nothing there is just a blinking cursor and I can't even type...

---

### Post by spiderbatdad on 2009-04-27
looks like a bug in grub and its support of the ext4 filesystem.
applying the patch might be tricky...you'll have to mount your filesystem from the live cd. If your installation is new, it might be easier to reinstall...I hate to say that. Then run apt-get update apt-get upgrade.
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/314350](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/314350)says a fix was released, so not sure why you are having this issue, unless you installed from an alpha release.

---

### Post by thegr8brian on 2009-04-27
I would really hate to have to reinstall...where can I find out how to patch it?

---

### Post by spiderbatdad on 2009-04-27
edited previous post with  link. don't know how to guide you on what file to patch,,,probably in the file /boot/grub/ext4 or such...you might post to the thread in launchpad for more help. generally you copy the patch, cd into the directory and run the command to apply the patch...this is of course after you have mounted the file system from the live cd.
you can download the file using the live cd.
pop in your cd and run;
sudo mount /dev/sda5 /mnt
copy the file: sudo cp ext4.patch /mnt/boot/grub
then cd into /mnt/boot/grub
apply patch:
patch -p1 < ext4.patch

instructions are probably not entirely perfect.

---

