---
title: "kdestartupconfig troubles.."
date: 2006-01-19
forum: General Help
---

### Post by Mathias-K on 2006-01-19
My HDD is partitioned into this:

hda1 = root drive -> Kubuntu 5.10, (For everyday working)
hda2 = /windows --> A big FAT32 trashheap for interswitching files
hda3 = Edubuntu 6.04 Flight 2 (i really like the concept, so i snooze around a little :))
hda4 = Trash/Test/Crash-partition

When Flight3 came online i immediately got the Edubuntu version, and it worked fine on the hda2 partition, but when i cleared hda4 and installed Kubuntu F3 on it, my hda1 root partition became somehow compromised! :confused:

When i boot it up, i get to the login screen, but when i've pressed my password, an error like this comes up:

~"Could not start kdestartupconfig. Please check the install." 

Can i somehow repair this, and what is the cause of it?

Thanks in advance for your time,
Mathias :)

---

### Post by Mathias-K on 2006-01-20
I have tried several things, including: 

sudo dpkg-reconfigure xserver-xorg
sudo apt-get update
sudo apt-get upgrade

I have not had any luck. Any ideas?

---

