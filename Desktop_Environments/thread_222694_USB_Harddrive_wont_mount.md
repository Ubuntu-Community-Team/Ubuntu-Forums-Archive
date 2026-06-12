---
title: "USB Harddrive wont mount"
date: 2006-07-25
forum: Desktop Environments
---

### Post by mcphatty on 2006-07-25
I know there are many topics on the subject, but I cant seem to find one that has the same problem I'm having, so hopefully someone here can help me out.

I'm a new user to Ubuntu, and am loving it. I'm dual-booting Windows XP and Ubuntu, with an external 160GB harddrive. I use the external drive for all my files such as music and movies. Until this morning, the drive worked fine. I was listening to music off of it before I went to bed, and once I booted up this morning, the drive didnt mount. I get the error:

mount: only root can mount /dev/sdd1 on /media/sdd1

being completley new to linux, I dont know what this means, and it's driving me nuts. The drive still works in Windows.

Any help?

---

### Post by taurus on 2006-07-25
Run the mount command with sudo...

```

sudo mount -t vfat /dev/sdd1 /media/sdd1
(and when it asks for a password, use the same one that you log in with...)

```

---

