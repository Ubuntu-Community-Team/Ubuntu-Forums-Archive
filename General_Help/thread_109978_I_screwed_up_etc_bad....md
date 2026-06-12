---
title: "I screwed up /etc/ bad..."
date: 2005-12-29
forum: General Help
---

### Post by Mazin on 2005-12-29
I, not knowing how to use chmod properly, accidently recursivly set everything in the /etc/ folder to 0766.  Now, Ubuntu won't work, and I need to change it back.  I can't even sudo in Ubuntu because the sudoers folder is 0766.

I need to change it back, and obviously, everything had different things set.  Will it work to use "chmod -R 777 *" in /etc/?  I think the problem is because some things that are supposed to be executable aren't, so maybe if I just go nuts and set everything to 777 it'll work?

I'm running Knoppix currently, but when I go to use chmod on the hard drive, I get read-only and permission errors and what-not.  Any pointers?

---

### Post by psusi on 2005-12-29
Nope, it's time to either reinstall, or restore from backup.

---

### Post by sciurus on 2005-12-29
Remounting it r/w in Knoppix (I think you can do this by right clicking on the partition's desktop icon) and redoing the recursive chmod with 755 will probably make everything work. However, it's safer to reinstall.

Ubuntu could really use a repair permissions feature like OS X has.

---

### Post by Mazin on 2005-12-29
Well, I totally chmoded everything in /etc/ to 777, and now it works, more or less.  Synaptic Package Manager doesn't seem to work.  Is there any way I can reinstall it?  I would go to the package manager, but... it's dead.

---

### Post by steve.horsley on 2005-12-30
I think I read thta sudo won't play unless the sudo executable's permissions are exactly right. FYI, mine is:

steve@StevesPC:~$ ll /usr/bin/sudo
-rwsr-xr-x  1 root root 93076 2005-10-28 20:19 /usr/bin/sudo
steve@StevesPC:~$ ll /etc/sudoers
-r--r-----  1 root root 406 2005-10-15 01:05 /etc/sudoers

But my advice is to back up your data and re-install.

---

