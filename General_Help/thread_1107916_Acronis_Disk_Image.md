---
title: "Acronis Disk Image"
date: 2009-03-27
forum: General Help
---

### Post by elkade on 2009-03-27
Through some searching, I came across this application and wondered if anyone out there has tried it or is using it with some success?

It is a disk imaging app. that I have used on the Windows side and works very well.  I went to there site and seems to be one avail. for Linux.

This is the name of the app.  Acronis TrueImage 8 0 Linux (Build 914)

Thanks for anyones help with this.

I have tried Flyback, but has some issues.  Can be discussed in another thread.

Thanks,

Larry

---

### Post by HavocXphere on 2009-03-27
I've had good luck with the Acronis imaging software. Does what it says on the box.

Do note that it doesn't like some hardware setups. So do download a trial first.

The current version isn't v8 though.

And I don't think there is a linux version per se. Since it is a *boot* disk, it runs independent of the OS installed. And it can read/restore both MS/linux filesystems.

There is also clonezilla, but I have not experience with it.

---

### Post by Ericyzfr1 on 2009-03-27
I have used Acronis True Image 10 and works great with XP and used to work great with Linux, not anymore. The only option you have is a cluster to cluster which takes a long time, not mentioning the file size. At the start it will tell you that your partition have errors, a user from another forum help me found out that Linux in preparation for EXT4 changed the i-nodes from 128k to 256k and Acronis does not recognize it. The workaround is to format your partition with 128 inodes.

---

