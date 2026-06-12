---
title: "Pure-ftpd"
date: 2009-01-01
forum: General Help
---

### Post by Cl0cKw0rK on 2009-01-01
pure-ftpd starts at startup. its not in the .bashrc in my home, or the rc in the init.d i need to find it so i can add some startup parameters. Any idea where it is or how to find it?

---

### Post by cmnorton on 2009-01-01
It's daemon is probably in /etc/init.d.

Edit:
---------------------

This recent post might also be of help to you. You have not indicated user login problems, but this link has a link to documentation on pure-ftp's web site.

[http://ubuntuforums.org/showthread.php?t=1024869](http://ubuntuforums.org/showthread.php?t=1024869)

---

### Post by Cl0cKw0rK on 2009-01-01
yes, that where the program is, but i need to find the file that is executing it. i need to add options to it.

---

### Post by cmnorton on 2009-01-02
Like other Linux software, it seems you would add options to the daemon.

---

