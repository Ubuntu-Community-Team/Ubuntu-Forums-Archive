---
title: "can i link my server to my workstation so the server doesnt have to host  files?"
date: 2009-06-13
forum: General Help
---

### Post by uberlube on 2009-06-13
Just like the title. Is this possible?

---

### Post by Jose Catre-Vandis on 2009-06-13
Don't really understand this - isn't that the whole point of a server - to host files?

Please more info about what you want to acheive :)

---

### Post by akakingess on 2009-06-13
> **Jose Catre-Vandis said:**
> Don't really understand this - isn't that the whole point of a server - to host files?

Please more info about what you want to acheive :)
+1 for Jose Catre-Vandis

Are you just wanting to connect them to chat, or share files both ways, or just wanting to set up the server as a "domain" server that doesn't actually host any files. We definitely need some more information as to what your goal is in the long run.

akakingess

---

### Post by uberlube on 2009-06-13
unfortunetelly my server box only has a 30g HD so its not the greatest for hosting. I was just curious if i could somehow mount a partition on my workstation so that it could be accessed by people connecting to my server via ssh.

---

### Post by akakingess on 2009-06-13
Yes, you should be able to mount it, then once it is mounted edit fstab and add the dev, i.e. media/disk1 to the bottom of the list and it should auto mount on startup.

akakingess

---

### Post by uberlube on 2009-06-13
yes but the partition is on my workstation and not on the serverbox

---

### Post by ubersolid on 2009-06-13
[http://www.debian-administration.org/articles/165](http://www.debian-administration.org/articles/165)

Or, you could go the easy way and exchange harddrives, put the larger one in the server if you don't need the space on your workstation.

Edit, I have not tried the link above, or the instructions it gives and I can't guarantee that anything in it works.

---

### Post by 3rdalbum on 2009-06-13
I'd run Samba or NFS on the workstation, and have the server mount the workstation's share into a location inside the server's share. Bit messy, but it should work.

The best solution is to put a bigger hard disk into the server. My home server runs off an 8GiB flash drive, but shares files off a 1TiB HDD. They are so cheap these days. You could easily run your server off the 30GiB HDD and share files off a big internal or external drive.

---

### Post by uberlube on 2009-06-13
> **3rdalbum said:**
> I'd run Samba or NFS on the workstation, and have the server mount the workstation's share into a location inside the server's share. Bit messy, but it should work.

The best solution is to put a bigger hard disk into the server. My home server runs off an 8GiB flash drive, but shares files off a 1TiB HDD. They are so cheap these days. You could easily run your server off the 30GiB HDD and share files off a big internal or external drive.


Ya ive got a 250 gig external that decided it only want to work when it wants to leately so ive just been inquiring into a temp fix for the time being. The samba server sounds interesting.

---

### Post by Jose Catre-Vandis on 2009-06-13
imho, NFS is the most solid and easy solution:

[http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS](http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS)

---

