---
title: "How do I uninstall Ubuntu Tweak?"
date: 2009-02-12
forum: General Help
---

### Post by jpcafazza on 2009-02-12
I can find it under add/remove apps... can some one help me out here?

---

### Post by Therion on 2009-02-12
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

---

### Post by jpcafazza on 2009-02-12
where does it talk about uninstalling it?

---

### Post by crillman on 2009-04-08
sudo dpkg -r ubuntu-tweak

---

### Post by sdb2028 on 2009-09-13
Having problems with Ubuntu Tweak. Install did not work and cannot remove it.
Here is the error from terminal when trying to remove:
sudo dpkg -r ubuntu-tweak
dpkg: error processing ubuntu-tweak (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ubuntu-tweak

Synaptic will no longer work, shows an error with Ubuntu Tweak then closes.
Any help would e appreciated.

---

### Post by DamagedGoods on 2009-10-16
I tried 

sudo dpkg -P ubuntu-tweak

and now states that it has been removed

---

### Post by jaime2009 on 2009-10-31
i try this but not work

jaime@jaime-desktop:~$ sudo dpkg -P ubuntu-tweak
(A ler a base de dados ... 132730 ficheiros e directórios actualmente instalados.)
A remover ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: erro ao processar ubuntu-tweak (--purge):
 subprocesso pre-removal script retornou erro do status de saída 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: erro enquanto limpava:
 subprocesso post-installation script retornou erro do status de saída 2
Foram encontrados erros enquanto processava:
 ubuntu-tweak
jaime@jaime-desktop:~$

---

### Post by kartikjagdale on 2010-10-31
I had the same problem

my update-manager ,Synaptic packet manager crashed due to ubuntu-tweak

I removed it using the command:
sudo dpkg -r ubuntu-tweak

it removed the ubuntu-tweak

but didn't solve the problem of crashing of other application

Can any one help me please

---

### Post by makotze on 2011-02-03
First run

 sudo dpkg -r ubuntu-tweak

then 

sudo dpkg -P ubuntu-tweak

then

I went into the etc - > apt -> source.list.d and deleted the Ubuntu tweak file [not sure what the name is anymore :)], and that fixed it. im on 10.10.

---

### Post by ksaboda on 2012-06-23
makotze, spot on with the removal instructions. That worked perfectly for me. Ironic the application that is for "everyone" has an uninstall procedure that is not.

---

