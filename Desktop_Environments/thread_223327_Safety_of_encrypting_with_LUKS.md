---
title: "Safety of encrypting with LUKS"
date: 2006-07-26
forum: Desktop Environments
---

### Post by auricle on 2006-07-26
I have a separate hard drive which I use for the /home directory. I am thinking of encrypting it using LUKS. I have never used disk encryption before and so I have a question!

If I reinstall Kubuntu on my root drive, will I be able to mount my encrypted home drive as I did previously?

I am concerned that some sort of configuration file stored elsewhere in the filesystem would get wiped leaving me with an unreadable /home drive.

Can anybody clarify this for me?

---

### Post by auricle on 2006-07-27
bump - anybody have any ideas?

---

### Post by gnomeza on 2006-11-12
You won't be able to mount your home directory *exactly* as you did before.
You'll either have to enter a passphrase on boot, or delay mounting the home directory until you login (for which you'll need to read up on the pam_mount plugin).

But to clarify: aside from the key itself, all information needed to mount a LUKS formatted drive is held on the drive itself. You won't lose the ability to mount it by reinstalling your root system.

---

