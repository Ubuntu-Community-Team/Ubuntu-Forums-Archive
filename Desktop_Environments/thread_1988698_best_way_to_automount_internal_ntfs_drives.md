---
title: "best way to automount internal ntfs drives?"
date: 2012-05-28
forum: Desktop Environments
---

### Post by idiotprogrammer on 2012-05-28
Hi, there I installed the latest ubuntu on one of my drives. Within nautilus I can see and explore various NTFS  hard drives from my dual boot windows. 

At the same time, I'm getting a lot of system crashes when an application is trying to access multiple files from these ntfs drives. 

when I access them through file explorer, they seem to be mounted, but somehow they don't seem to be mounted -- or at least have a lag time in accessing these files. 

Am I correct that when apps are dealing with unmounted drives, that tends to cause crashes? 

What's the best way to automount ntfs drives. just by editing /etc/fstab or are there some user friendly system tools to let me automount some at startup?

---

### Post by nipunshakya on 2012-05-28
This might solve your issue of auto mounting ntfs drives:
[http://ubuntuportal.com/2012/05/heres-two-methods-to-mount-automatically-ntfs-drive-in-ubuntu-12-04.html](http://ubuntuportal.com/2012/05/heres-two-methods-to-mount-automatically-ntfs-drive-in-ubuntu-12-04.html)


Happy Linuxing

---

### Post by Morbius1 on 2012-05-28
>  What's the best way to automount ntfs drives. just by editing /etc/fstab  or are there some user friendly system tools to let me automount some  at startup?Unfortunately the "user friendly system tools" are either broke or do silly things which is why I recommend templates.

Here is the template:
```
 UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```
[COLOR=Blue]*Note: If you have mounted the partition manually already please unmount it.*[/COLOR]

[1] To find the correct UUID number:
```
sudo blkid -c /dev/null
```[2] You will have to create the mount point yourself, for example:
```
sudo mkdir /media/WinD 
```[3] Then add the template with the correct UUID and mount point to fstab:
```
gksu gedit /etc/fstab 
```[4] And when you are done editing fstab and saving it run the  following command to test for errors and mount the partitions without  requiring a reboot.  You will know before you reboot if something is  amiss. :
```
sudo mount -a
```You will never have to rely on a poorly written utility again, you will gain an approving nod from the elder-geeks and become more attractive to those that matter. You will also grow taller, make more money, be able to retire early, and much later on in life your grandchildren will actually want to come over to visit you.

---

### Post by coffeecat on 2012-05-28
> **Morbius1 said:**
> You will never have to rely on a poorly written utility again, you will gain an approving nod from the elder-geeks and become more attractive to those that matter. You will also grow taller, make more money, be able to retire early, and much later on in life your grandchildren will actually want to come over to visit you.

... and you will save the life of a kitten! :wink:

But seriously, I'm concerned about this bit of your post:

> **idiotprogrammer said:**
> At the same time, I'm getting a lot of system crashes when an application is trying to access multiple files from these ntfs drives. 

when I access them through file explorer, they seem to be mounted, but somehow they don't seem to be mounted -- or at least have a lag time in accessing these files. 

Am I correct that when apps are dealing with unmounted drives, that tends to cause crashes? 


Filesystems are either mounted or not mounted, and the only practical difference that you should see between mounting NTFS filesystems from the file browser or mounting by means of /etc/fstab is the mount options, which may or may not be an issue with some applications. You shouldn't be seeing any lag when accessing files from a NTFS partition mounted from the file browser and system crashes are worrying. And with regard to your last sentence in the quote, if an app is trying to access a file from a partition which is not mounted, you should see, at worst, an error message. Which apps are causing crashes when they try to access files from unmounted partitions?

---

### Post by idiotprogrammer on 2012-06-04
Thanks for your reply and your thoughts about crashing and automounting. 

I mainly had this happen when I was trying to run dropbox or RhythmBox or the video player  when the hard drive needed to be accessed by the program was unmounted. 

But now that you mention, i think you are right that the mounting issue and the crashing issue are separate (though I haven't had any crashes since I fixed the automount configuration issue).

---

