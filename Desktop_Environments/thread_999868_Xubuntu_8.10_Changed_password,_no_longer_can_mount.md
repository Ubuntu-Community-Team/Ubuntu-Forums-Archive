---
title: "Xubuntu 8.10: Changed password, no longer can mount CDROM"
date: 2008-12-02
forum: Desktop Environments
---

### Post by crypticlabs on 2008-12-02
**BACKGROUND**

I am running Xubuntu 8.10 on a Dell Inspiron 700m. I changed my password using the 'passwd' command. After doing so and after the next time I rebooted and logged into the computer, the NetworkManager was trying to use the default keyring but due to a lock, it was asking me for a password. My original password would work and it would continue to connect to my wireless network. I did some searching on how to make it not ask me for a password and what I found was to delete the .gnome2/keyrings/login.keyring file. I did this, rebooted, logged in, the NetworkManger asked me for my wireless key, and all is back to normal. No more prompts for passwords.

**PROBLEM**

I can no longer mount a CD. I am getting a "failed to mount message, mount: mount point /media/cdrom0 does not exist.". I believe this has something to do with the keyring. I replicated this whole process on my desktop which runs Ubuntu 8.10 and almost the same thing...I don't get an error message but the CD will not mount. I know that my CDROM does work as I've tried multiple known working discs as well as booted my laptop into a Ubuntu Live disk.

Please help to get my CDROM working again :)

---

### Post by mali2297 on 2008-12-02
Does the directory /media/cdrom0 exist?

If not, create it with
```

sudo mkdir /media/cdrom0

```

---

### Post by crypticlabs on 2008-12-02
mali2297 -

It's funny you should say that. I just figured out what the problem is right before you posted that.

It turns out it has nothing to do with keyring, it's all just a matter of coincidence. I am using autofs to mount some NFS shares, namely Music and Videos. I configured my /etc/auto.master file to mount them in /media, thinking that was a good general name for Music and Videos...and not thinking that folder (/media) was already in place and when using autofs, the parent directory chosen for the mount should not already exist, as autofs will create it.

I stopped autofs and /media showed up with cdrom and cdrom0 and I can now access the CDROM.

---

