---
title: "Sudo su slowly asking password"
date: 2009-02-21
forum: General Help
---

### Post by cd-r80 on 2009-02-21
Can somenone tell why in Intrepid sudo su asking password is slow?

---

### Post by Sprut1 on 2009-02-21
> **cd-r80 said:**
> Can somenone tell why in Intrepid sudo su asking password is slow?

?

It's fast as a cheetah here.

---

### Post by Armor Nick on 2009-02-21
On a general note, changing to root with sudo su is bad computer use. If you really must change to root, use sudo -i (use your own password).

---

### Post by cd-r80 on 2009-02-22
Ok it asks fast, but it takes ages to check password. why sudo su is bad?

---

### Post by Sprut1 on 2009-02-22
> **cd-r80 said:**
> Ok it asks fast, but it takes ages to check password. why sudo su is bad?

As Armor Nick said, you shouldn't be using sudo su - rather use sudo to become root temporarily.

---

### Post by mcduck on 2009-02-22
"sudo su" or "sudo -s" won't load root user's environment variables correctly, which means that it's using you normal user's environment instead (although with root permissions). Depending on what you do this can lead into troubles. Like some of your personal configuration files being overwritten with root permissions, for example..

"sudo -i" loads all environment variables correctly, acting just like a normal interactive login shell.

(there's an easy example of the difference, running "sudo su" or "sudo -s" will keep you in the current directory, while "sudo -i" moves you to /root just like a login shell should do.)

What comes to the slowness, I can't say anything about that. I would probably start by making sure that /etc/hosts is configured correctly, as having wrong settings for localhost can cause all kinds of slowdowns and delays.

---

