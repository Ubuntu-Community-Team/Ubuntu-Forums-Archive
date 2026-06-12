---
title: "Mounting ISO's"
date: 2011-01-20
forum: Desktop Environments
---

### Post by motermouth15 on 2011-01-20
Today i was installing a virtual machine through VirtualBox OSE, and i had been doing so by a mounted iso from my ubuntu server's file share. My roommate was about to do the same thing, however, had made the comment that once it was mounted he could only see one file in it and it was a readme.txt file. After looking into it every linux machine that i have will only mount the image (saying that its 4.3gb) however only show that one file, even the original one that i started on. The weird part is that my mac can connect to the same file share and mount the same image, however, see the whole thing. Any ideas?

-Nate

---

### Post by nomko on 2011-01-20
> **motermouth15 said:**
> Today i was installing a virtual machine through VirtualBox OSE, and i had been doing so by a mounted iso from my ubuntu server's file share. My roommate was about to do the same thing, however, had made the comment that once it was mounted he could only see one file in it and it was a readme.txt file. After looking into it every linux machine that i have will only mount the image (saying that its 4.3gb) however only show that one file, even the original one that i started on. The weird part is that my mac can connect to the same file share and mount the same image, however, see the whole thing. Any ideas?
 
-Nate
 
Why using the OSE version of VirtualBox? The OSE version has some limitation which the non-OSE version doesn't have.
 
Install the "full" version of VirtualBox, go to this site: [www.virtualbox.org]("http://www.virtualbox.org").

---

### Post by motermouth15 on 2011-01-20
Thanks but that still doesn't solve my ISO mounting problem...

---

### Post by Krytarik on 2011-01-21
How do you mount the ISO then?

---

### Post by motermouth15 on 2011-01-21
If you right click on an ISO (lets say its on my server), and click the 'Archive Mounter' option, the ISO is mounted to your desktop. However now that my problem has started, it continues to say that my ISO is 4.3gb but when i open it up i can only see a README.txt file.

---

### Post by Krytarik on 2011-01-21
Try to mount it manually, like this:
```
sudo mount -o loop -t iso9660 foo.iso /mountpoint
```

Or use one of those GUIs, I have personally have once used Furius:
[http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html)
[http://www.ubuntugeek.com/furius-iso-mount-mount-and-unmount-iso-images-with-gui-tool-in-ubuntu-linux.html](http://www.ubuntugeek.com/furius-iso-mount-mount-and-unmount-iso-images-with-gui-tool-in-ubuntu-linux.html)

---

### Post by motermouth15 on 2011-01-23
Dude i just tried the furius one and i still have the same problem. it mounts the iso but the iso mounted only has the one file.

---

### Post by Krytarik on 2011-01-23
Could it be that the iso is corrupt? What about extracting it's content with the Mac and writing a new one?

---

### Post by motermouth15 on 2011-01-25
> **Krytarik said:**
> Could it be that the iso is corrupt? What about extracting it's content with the Mac and writing a new one?

So then that would mean that every iso file that i have (close to 100) are all suddenly corrupted. Every other computer I own, along with this one before it quit working, mounted them with no problem.

My mac, my windows xp, along another ubuntu machine can still mount them without a problem.

---

