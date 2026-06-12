---
title: "Ext4 FS vs Ext3 FS"
date: 2009-04-23
forum: General Help
---

### Post by NekoMaster on 2009-04-23
I wanna know how reliable Ext4 is right now, since it seams like its a bit faster and can handle more, plus its for (as far as i know) 64bit Ubuntu

---

### Post by Paqman on 2009-04-23
Ext4 is officially marked stable, but there's still a couple of kinks to iron out. If it's a machine that you want to be stable, stick to ext3. If you can handle a small amount of risk for a performance boost, go ext4.

Ext4 is for any type of machine, not just 64-bit.

---

### Post by bodhi.zazen on 2009-04-23
This is a recurring question as of late :)

You will get varying opinions

[[all variants] Ext3 and Ext4: Which file system to install? - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=7125328#post7125328")

---

### Post by Rainstride on 2009-04-23
all the major bugs iv seen have been ironed out, but it is a new file system so there might be some small bugs lurking in the shadows.

---

### Post by Paqman on 2009-04-24
> **Rainstride said:**
> all the major bugs iv seen have been ironed out, but it is a new file system so there might be some small bugs lurking in the shadows.

I'm using it myself, but there is this caveat in the [Jaunty release notes](http://www.ubuntu.com/getubuntu/releasenotes/904):
> 
Lock-ups when deleting files from ext4 filesystems

In some cases, deleting files from an ext4 filesystem is reported to cause soft lock-ups in the kernel (330824). Investigation of this problem is ongoing, and it is expected that a fix for this problem will be made available as a post-release update. To avoid this problem, users may wish to install using the default ext3 filesystem and convert their filesystem to ext4 (as documented on the ext4 wiki) once a fix is available. 


---

