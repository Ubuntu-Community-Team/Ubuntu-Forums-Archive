---
title: "What does /var/run and /var/lock do?"
date: 2009-02-12
forum: General Help
---

### Post by hardysummer on 2009-02-12
Some distros that I have tried does not even have or mount this.  What does /var/run and /var/lock do?  And how is this mounted?  It is not located in the /etc/fstab.

---

### Post by lykwydchykyn on 2009-02-12
/var/run basically is used to store .pid files, which contain the process id of a running program.  This is commonly used in services or other programs that need to make their process id's available to other processes.

/var/lock is used to store lock files, which are simply files used to indicate that a certain resource (a database, a file, a device) is in use and should not be accessed by another process.  Aptitude, for example, locks its database when a package manager is running.

Both directories contain very small throwaway files that are frequently created or destroyed, so instead of taxing your hard drive with all that activity, they are mounted to a ram drive.  A ram drive is just a chunk of your system memory which the OS can treat as if it were a storage device.

clear as mud?

---

