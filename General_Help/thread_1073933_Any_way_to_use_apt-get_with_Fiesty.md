---
title: "Any way to use apt-get with Fiesty?"
date: 2009-02-18
forum: General Help
---

### Post by pkulak on 2009-02-18
So, realize that my install is no longer supported, but I had no idea the repos would disappear. I just need to install something really tiny any simple (PHP curl), but I'm at a loss here. Upgrading/reinstalling isn't really an option since it would take me about a week to fix everything that will break if I do that. Thanks for any help!

---

### Post by taurus on 2009-02-18
You need to edit your /etc/apt/sources.list to point to here, [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/) for feisty.

---

### Post by pkulak on 2009-02-18
Did you mean: [http://old-releases.ubuntu.com/ubuntu/?](http://old-releases.ubuntu.com/ubuntu/?) Because that seemed to work. Thanks!

---

### Post by taurus on 2009-02-18
Yes, replace the current https in /etc/apt/sources.list with the new lines, pointing to the old-releases repos.

---

### Post by geirha on 2009-02-18
Feisty is no longer supported though, so you should really consider upgrading to a supported release: [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by bodhi.zazen on 2009-02-18
taurus : Are there any packages ?

---

### Post by Yellow Pasque on 2009-02-18
Are you using this computer as a server? If so, install Ubuntu 8.04/Hardy if possible.

---

### Post by wildman4god on 2009-02-18
I am also going to ask why you wouldn't upgrade to a new ubuntu version?

---

### Post by pkulak on 2009-02-19
> **wildman4god said:**
> I am also going to ask why you wouldn't upgrade to a new ubuntu version?

I've tried upgrading, but apt just freaked out and died. Probably because the repos didn't exist anymore, but I don't really want to try again if I've got everything I need working. I've got a custom Apache compile running a couple websites, it's a file server with Samba, Netatalk and Webdav, a print server, a web proxy, and probably a dozen other things I will forget about until they break. If you can guarantee that nothing will break, I'll do it, but I work with computers for a living and I don't really want to take a weekend doing nearly the same stuff I do at work, not getting paid for it, and not getting to do something fun instead. Plus pissing off my wife until I at least get the print server up and running again.

Seems like a good reason, right?

EDIT: And yes, had I to do it all over again, and the next time I _do_ update, I'd have used a LTS release.

---

### Post by wildman4god on 2009-02-20
backup your data, and download the 8.10 iso and to a fresh install, thats how I do all my upgrades.

---

### Post by dcstar on 2009-02-20
> **pkulak said:**
> I've tried upgrading, but apt just freaked out and died. Probably because the repos didn't exist anymore, but I don't really want to try again if I've got everything I need working. I've got a custom Apache compile running a couple websites, it's a file server with Samba, Netatalk and Webdav, a print server, a web proxy, and probably a dozen other things I will forget about until they break. If you can guarantee that nothing will break, I'll do it, but I work with computers for a living and I don't really want to take a weekend doing nearly the same stuff I do at work, not getting paid for it, and not getting to do something fun instead. Plus pissing off my wife until I at least get the print server up and running again.

Seems like a good reason, right?


A major point about supported releases is that all the discovered security vulnerabilities are patched and made available in the updates.

Since you have an unsupported server connected to the Internet you now have a server that is vulnerable to any security issues discovered since the last time it was updated, is that really a good situation?

You should install 8.04 server, it is a LTS that will be supported until 2013.

---

### Post by pkulak on 2009-02-23
> **dcstar said:**
> A major point about supported releases is that all the discovered security vulnerabilities are patched and made available in the updates.

Since you have an unsupported server connected to the Internet you now have a server that is vulnerable to any security issues discovered since the last time it was updated, is that really a good situation?

You should install 8.04 server, it is a LTS that will be supported until 2013.

Well, here's another problem. If you know a way around it, I'd really appreciate it. And it'll get me to upgrade for ya. :D

I've got three drives in this box. Two identical 120-gigs, and a 300-gig. I've got / on one 120-gig and /home on the other. I printed out my fstab, thinking it would come in handy in choosing the drive to do the reinstall on, but the Hardy installer just listed two 120-gig drives with the exact same model number. No unique ids, mount points, free-space or anything that I could use to tell them apart. A 50% chance of wiping out my home drive isn't really an option for me. :D

---

### Post by geirha on 2009-02-23
Switch to another console with Alt+F2, then mount one of the partitions temporarily.
```
sudo mount /dev/sda1 /mnt
ls /mnt
sudo umount /dev/sda1
```

Do that for all partitions until you know which one is which, then switch back to the installer with Alt+F1.

---

### Post by pkulak on 2009-02-24
> **geirha said:**
> Switch to another console with Alt+F2, then mount one of the partitions temporarily.
```
sudo mount /dev/sda1 /mnt
ls /mnt
sudo umount /dev/sda1
```

Do that for all partitions until you know which one is which, then switch back to the installer with Alt+F1.

Oh, great idea. Thanks!

---

### Post by ibuclaw on 2009-02-24
You do know that the great thing about Open Source is that you are free to use whatever you want, without any pressure about whether or not you should decide about upgrading. (I still have a computer running Debian Woody).

I personally wouldn't sway to people here asking "Why not upgrade to Intrepid? Why not try Hardy?"
If what you already have works for you, then that is good enough reason why you should leave it be :)

Although, I do have to admit that I've never had an issue with running
```
sudo update-manager -d
```
And doing a Distribution Upgrade from:
Edgy -> Feisty
Feisty -> Gutsy
Gutsy -> Hardy

In the space of about 3 hours, all because I don't have any spare CDs, and the Edgy installer was all I could find :D

Regards
Iain

---

### Post by pkulak on 2009-02-25
> **geirha said:**
> Switch to another console with Alt+F2, then mount one of the partitions temporarily.
```
sudo mount /dev/sda1 /mnt
ls /mnt
sudo umount /dev/sda1
```

Do that for all partitions until you know which one is which, then switch back to the installer with Alt+F1.

That doesn't seem to work. There's no sudo, but when I try just


```
sudo mount /dev/sdb /mnt
```

I get "mounting /dev/sdb on /mnt failed: Invalid argument", which is odd, because I didn't supply any arguments...

---

### Post by pkulak on 2009-02-25
Nevermind. I had to mount them as sdb1 and sdc1. Then it worked like a charm!

---

