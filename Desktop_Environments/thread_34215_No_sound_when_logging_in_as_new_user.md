---
title: "No sound when logging in as new user"
date: 2005-05-13
forum: Desktop Environments
---

### Post by banjobacon on 2005-05-13
When switching users (by going to Applications > System Tools > New login), the new user does not get any sound. This user belongs to the audio group, and sound works properly when logging in normally. The problem is when there is more than one user logged in at once.

Is this a known issue with a solution?

Thanks.

---

### Post by harryc on 2005-05-13
It's a known problem with no real solution other than switching to OSS or Alsa when sound is required for the 'other' users apps. The downside is that there is no mixing and two programs trying to produce sound simultaneously may throw up errors at you.

[http://ubuntuforums.org/showthread.php?t=17266&page=1&pp=10&highlight=sound+users](http://ubuntuforums.org/showthread.php?t=17266&page=1&pp=10&highlight=sound+users)

---

### Post by g14 on 2005-05-15
There *IS* a solution to this.

Basically, esd expects to be run once per-machine, and doesn't allow for
multi-user setups. The simple answer is to edit /etc/esound/esd.conf and add
`-unix -promiscuous' (no quotes) to the default_options value. This should force
the first users' esd process to allow other users play sounds. After that, you need to do sudo telinit 1 and then telinit 2, or just reboot. Then it will work.

---

