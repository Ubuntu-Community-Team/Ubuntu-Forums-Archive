---
title: "umount permissions"
date: 2009-03-06
forum: General Help
---

### Post by Coding Monkey on 2009-03-06
Hi guys

This question has probably been asked before, but none of the threads that I could find explained it to me clearly (I am fairly new to Ubuntu, and Linux in general).  I am able to mount a network drive through the terminal using the smbmount command, using a credentials file, thus mounting the drive without having to type a password into a prompt.  However, when try to unmount the drive through the terminal using the umount command.  I get the following error "<my mount name> is not in the fstab (and you are not root)".  Could anyone please tell me how to unmount the drive without using sudo, and if possible, without having to edit the fstab.

Thank you

---

### Post by beno1990 on 2009-03-06
Instead of using the command umount, use umount.cifs.

Read more about the command with

```

man umount.cifs

```

umount is only for local filesystems.

---

### Post by Coding Monkey on 2009-03-06
Brilliant!  Thank you very much. :D

---

