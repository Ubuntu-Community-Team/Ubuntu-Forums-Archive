---
title: "Dual Boot Ubuntu and Xubuntu- Grub problem"
date: 2007-02-16
forum: Desktop Environments
---

### Post by cmulax on 2007-02-16
So I have a perfectly stable and running hard drive with ubuntu on it, and I wanted to give xubuntu a try on my second hard drive.  I successfully installed xubuntu on it using the 6.10 live cd, however grub only shows the xubuntu os.  I know for a fact that everything in my first hard drive is intact, as I can mount it and use everything in it, but I am at a loss as to how to fix grub to add my first hard drive back into it.

Any help would be appreciated!

---

### Post by scrooge_74 on 2007-02-16
Humm it seems you miss something somewhere, I have Edgy Xubuntu and Dapper Ubuntu living in the same disk on diferent partitions.

Take a look at these
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

---

### Post by Resurrection on 2007-02-16
Yeah I think those threads will help you.

My guess as to what went wrong was that you allowed Xubuntu to install Grub for you without it taking into account that you already had grub installed for Ubuntu.  

I would go by the thread that says to restore Grub for Ubuntu, and then just modify your /boot/grub/menu.lst file to add an entry to boot Xubuntu.  To make it easier if you are not sure what to do, you may want to post here what it says currently in your /boot/grub/menu.lst file on the Xubuntu hard drive and then folks here can help you modify the Ubuntu grub once you get it fixed.

This makes sense as the way to go, as you want Ubuntu to be the main distro that works so that if you don't like Xubuntu you can just wipe that drive without any issues.

---

