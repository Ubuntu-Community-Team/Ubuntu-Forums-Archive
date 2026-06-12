---
title: "Removing Permission froma Home Folder and partition"
date: 2009-04-01
forum: General Help
---

### Post by srkelley on 2009-04-01
I just deleted all of the partitions I had instaalled but the home partition. I can't copy anything from the home partition because of the permissions. I've tried changing them, but am unable to do so. I'm currently in a live environment with Lubuntu. The LXDE based version of Ubuntu 7.10/8.04. It works great, but I don't know how to get these permissions changed. Could someone out there please help me?

---

### Post by steeleyuk on 2009-04-01
Open a terminal and type:

sudo chown -hR ubuntu /path/to/home/directory

That usually works on the Ubuntu Live CD for me. I'm presuming that the LXDE based version uses a user called ubuntu to log in.

---

### Post by srkelley on 2009-04-01
Thank you, it's worked perfectly. Here, have some popcorn :popcorn:. thank you.

---

