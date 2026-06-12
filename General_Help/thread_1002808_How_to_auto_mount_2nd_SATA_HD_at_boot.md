---
title: "How to auto mount 2nd SATA HD at boot?"
date: 2008-12-05
forum: General Help
---

### Post by GmAz on 2008-12-05
Ok, I just had to redo my system because of a HD failure.  I reinstalled Ubuntu on a 250gb HD and installed a new 1tb drive for my pictured, music, video, etc.  I want that 1tb drive to auto mount when my system boots up.  I know I can easily mount it from the Places menu, but I share media to two other computers in my house and if I don't mount it, my wife gets mad because she doesn't know how to use Linux and doesn't want to touch my desktop.  So, how can I make it so the drive auto mounts?

---

### Post by pennacook on 2008-12-05
You can add it to your /etc/fstab to mount on boot.

```

/dev/<drive&partition>        /mount/point   <type of file system>     0       1

```

---

### Post by GmAz on 2008-12-05
Ok, I got it to mount, and it mounts after the restart.  Used this:
UUID=1270513D705128AD /media/Terabyte auto defaults 0 0

Now, is there a way I can rename the drive.  Right now its called 1000.2 GB Media.  I'd prefer to name it something else.  How can I achieve this?

---

### Post by taurus on 2008-12-05
What filesystem is that new 1TB drive?

---

### Post by GmAz on 2008-12-05
NTFS since I dual boot Vista64 to do video editing from time to time.  If I rename it in Vista, will it apply in Ubuntu too?

---

