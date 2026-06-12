---
title: "Unable to boot/recover - Invalid Group"
date: 2009-03-05
forum: General Help
---

### Post by naraht on 2009-03-05
So, I'm currently unable to boot my main computer.  It is locking up mid-boot, after filling the screen with several errors such as

chown: invalid group: `adm'
chown: invalid group: `root:utmp'
chown: invalid group: `root:polkituser'
chown: invalid group: `syslog:adm'



help?


Update:  letting it sit for several minutes, the machine does eventually boot...
first is a big error box saying GDM is misconfigured/no user

then I have to manually log onto the console, and startx, which then doesn't have mouse support, or sound, and several errors pop up, over each other, so I can't say which ones.

*sigh*

---

### Post by naraht on 2009-03-05
bump

---

### Post by naraht on 2009-03-05
anyone?

---

### Post by naraht on 2009-03-05
So...more information in the hopes that someone will eventually be able to help me...

at sonsole, I can't sudo, as it says my login isn't in the sudoers group.

id shows that my UID=1000  my gid=65534(nogroup) groups(65534 (nogroup)

---

### Post by naraht on 2009-03-05
fine...whatever...

time to reinstall.......

4 hours, no one even looked at the thread.

---

### Post by jellybaby on 2009-03-05
Hi,

    just saw your post. With so many confused permissions, I couldn't even begin to say what the problem is. First advice: try booting into "recovery mode"(in the Grub boot menu). This saved me twice when Ubuntu wouldn't start normally (don't even know what it did or what problems I was having; it just worked).

Good luck!

---

