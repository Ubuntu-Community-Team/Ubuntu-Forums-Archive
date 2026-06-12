---
title: "gnomebaker /mnt/cdrom error"
date: 2005-05-20
forum: Desktop Environments
---

### Post by Ainvar on 2005-05-20
Ok I am trying to format a dvd-rw in gnomebaker and I recieve this error.
[IMG]http://www.smugglingyoyos.net/ubuntuforums/Screenshot-Error.png[/IMG]

My cdrom is mounted at /media/cdrom (link) and /media/cdrom0
I have not found a place to tell gnomebaker that. I dont have this problem in k3b but would like to have all software installed on this system working correctly.

Any help would be appreciated. I did try searching for this in the forum and I do hate asking something that may already have been discussed but i did not find anything with the search strings I used that jumped out at me.

---

### Post by f.prisson on 2005-05-20
Perhaps it would help to do a sylink /mnt/cdrom pointing to /media/cdrom

---

### Post by Ainvar on 2005-05-20
unfortunately that does not fix it, I have already tried do a ln -s to both the /media/cdrom (link) and /media/cdrom0. I have also tried doing a ln -s from /.dev/scd0 and that did not work either. Guess k3b will be the winnar till this gets resolved.

---

### Post by f.prisson on 2005-05-20
The error sound as if gnomebaker doesn't find the device in /etc/fstab. Have you checked that there is an entry at the time you want to write to dvd?

---

