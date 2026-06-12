---
title: "GCC overwritten"
date: 2009-02-24
forum: General Help
---

### Post by Jdallen5 on 2009-02-24
I feel pretty stupid.  I apparently overwrote my gcc file with a different file using mv as root.  Is there a way to replace this file without reinstalling the whole program?  

If its necessary to reinstall, is it possible to get the program on a different computer and then move it over using a flash drive for instance?  Or is there another way to get the program installed on a computer that's not currently connected to the internet?

Thanks in advance for any info.  As soon as I realized what I did I about flipped out of my chair... lol

jdallen5

---

### Post by taurus on 2009-02-24
Did you remember which one and what is the new name?  You can reverse the process, changing the new name back to what it was before.

---

### Post by geirha on 2009-02-24
When you install a package through one of the package managers, it first downloads it from the repositories, then it installs it. The downloaded package does not get deleted, and it's kept under /var/cache/apt/archives. Unless you have run the command "apt-get clean" (which deletes all packages in /var/cache/apt/archives), the gcc-package should still be there, and running ```
sudo aptitude reinstall gcc
``` should reinstall the package without requiring internet access.

---

### Post by Jdallen5 on 2009-02-24
Well, I took a seperate text file and overwrote the /usr/bin/gcc file.  It shouldn't normally work, but like an idiot I forced it to as root.

---

### Post by snova on 2009-02-24
> **Jdallen5 said:**
> Well, I took a seperate text file and overwrote the /usr/bin/gcc file.  It shouldn't normally work, but like an idiot I forced it to as root.

That should be easy to replace, it's only a symlink.

```
sudo ln -s gcc-4.3 /usr/bin/gcc
```

Assuming it originally pointed to gcc-4.3 (which it does on my machine).

Quicker than reinstalling (even for a single package).

---

### Post by geirha on 2009-02-24
Hang on, you don't need to reinstall gcc. /usr/bin/gcc is just a symbolic link to the real executable, which is something like /usr/bin/gcc-4.3 or /usr/bn/gcc-4.2, depending on what ubuntu release you are running. Recreating that symlink is all that is needed.
```

# Find the gcc executable, either gcc-4.2 or gcc-4.3
ls /usr/bin/gcc-*

# then if it is gcc-4.3
sudo ln -s gcc-4.3 /usr/bin/gcc

```

---

### Post by Jdallen5 on 2009-02-24
Thankyou gentlemen, you saved the day!

:)

---

