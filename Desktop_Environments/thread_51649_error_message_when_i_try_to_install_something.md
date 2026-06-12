---
title: "error message when i try to install something"
date: 2005-07-24
forum: Desktop Environments
---

### Post by Silentkil on 2005-07-24
i got this when trying: 
sudo apt-get upgrade
i tried with other stuff.. still didnt help.. please help asap
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by evilghost on 2005-07-24
Shouldn't that be:
apt-get **update** not *upgrade*? ;)

---

### Post by Silentkil on 2005-07-24
[QUOTE=evilghost]Shouldn't that be:
apt-get **update** not *upgrade*? ;)[/QUOTE]
 yes ur right thats what i wrote... but i still got that message

---

### Post by Silentkil on 2005-07-25
[QUOTE=Silentkil]yes ur right thats what i wrote... but i still got that message[/QUOTE]
 i still am not getting it to work... can sum1 please help.. :-/

---

### Post by az on 2005-07-25
You may have a currupted database.

Try

sudo dpkg --clear-avail

and then update, upgrade, dist-upgrade, whatever..

---

