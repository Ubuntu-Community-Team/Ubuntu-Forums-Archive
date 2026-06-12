---
title: "How can I keep installed packages in sync across instalations"
date: 2009-02-22
forum: General Help
---

### Post by hypexr on 2009-02-22
Hello,

I have several boxes running ubuntu and I need to keep the same packages installed on all of these boxes. 

Is there anything as sexy as a tool that will let me apt-get a package on one box and it will automatically get installed on the other boxes?  Or even something as simple as a way to export a list of installed packages on one box, copy the list to another, and run something that would install/uninstall packages on the new box to make it match the origional?

Any ideas?

---

### Post by longtom on 2009-02-22
Good one - I second!

---

### Post by razy60 on 2009-02-22
would it not be better to run one box as a server then utilize that to do what you want.
Just asking as it seems the most obvious choice.

Raz

---

### Post by jnw222 on 2009-02-22
you can ssh across machines

---

### Post by Cheesemill on 2009-02-22
How about this:

[http://www.ubuntugeek.com/clone-your-ubuntu-installation.html]("http://www.ubuntugeek.com/clone-your-ubuntu-installation.html")

Also documented here:

[http://ubuntuforums.org/showthread.php?t=576629]("http://ubuntuforums.org/showthread.php?t=576629")

---

### Post by sofasurfer on 2009-02-22
HOW TO SAVE A PACKAGE LIST AND USE IT TO CLONE A LINUX SYSTEM
-------------------------------------------------------------

To save installed-packages-list to a file

dpkg --get-selections | grep -v deinstall > /home/username/Documents/linux/installed-packages-list

OR

Make sure backup partition is mounted.
dpkg --get-selections | grep -v deinstall > /media/disk/backup/Documents/linux/installed-packages-list
-----------------------------------------------------------------------------------------------------

To use installed-packages-list to clone a new linux installation

1) Reinstall base system
2) Copy entire network directory copied back to /etc/, sources.list copied back to etc/apt/
3) Open network config window and enter encryption key. You now have internet access.
4) sudo apt-get update
5) sudo apt-get dist-upgrade
6) dpkg --set-selections < /media/disk/backup/installed-package-list
7) sudo apt-get install dselect
8) sudo dselect
9) when prompted, choose to install packages

---

### Post by longtom on 2009-02-23
What about the other machines are not in different location without Internet access?

regards

longtom

---

