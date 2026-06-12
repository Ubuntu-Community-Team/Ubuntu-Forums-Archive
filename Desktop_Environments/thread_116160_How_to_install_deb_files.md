---
title: "How to install deb files ?"
date: 2006-01-12
forum: Desktop Environments
---

### Post by pfabrikant on 2006-01-12
Hey all,
after much work, I just managed to install openoffice deb.sh file ( a hebrew version of openoffice 2.0) from the internet to a directory through my computer. the file was named OOo_2.0_linux_install_he_deb.sh so, naturally I assumed it will install itself automaticaly. I used the command              'sh/cd directory name/name of file'             but all it did is to move the files from a deb.sh to several deb files. Now I have a collection of deb package files on my computer and I have no Idea how to install it so I could use the program itself.
What can I do ?
Thanks

---

### Post by psychicdragon on 2006-01-12
Deb packages can be installed with dpkg.

```
sudo dpkg -i name_of_package.deb
```

If you get an error about missing dependencies, run ```
sudo apt-get -f install
``` to hopefully get them all.

---

### Post by kaamos on 2006-01-12
You can install a deb with:
```
sudo dpkg -i name.deb
```
If you have a lot of files, you can move them into one folder and do
```
sudo dpkg -i /path/to/files/*.deb
```

---

### Post by asktoby on 2006-02-01
frm the apt-get manpage:
==========================
-f, --fix-broken
              Fix; attempt to correct a system with  broken  deâ
              pendencies  in  place. This option, when used with
              install/remove, can omit any  packages  to  permit
              APT  to deduce a likely solution. Any Package that
              are specified must completely correct the problem.
              The option is sometimes necessary when running APT
              for the first time; APT itself does not allow broâ
              ken  package dependencies to exist on a system. It
              is possible that a systemâs  dependency  structure
              can  be  so corrupt as to require manual intervenâ
              tion (which usually means using dselect(8) or dpkg
              --remove  to eliminate some of the offending packâ
              ages). Use of this option  together  with  -m  may
              produce an error in some situations. Configuration
              Item: APT::Get::Fix-Broken.
====================

Is there any risk to carrying out the command:
sudo apt-get -f install
?

The manpage uses words like 'corrupt', 'broken', 'manual intervention', 'error'... frankly it's scared me right off!

(I'm trying to install a *.deb and have a dependency problem.)

---

