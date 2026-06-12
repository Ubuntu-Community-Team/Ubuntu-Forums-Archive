---
title: "Openoffice runs only as root"
date: 2008-12-19
forum: General Help
---

### Post by AKoine on 2008-12-19
Hello,

I recently received my Dell mini 9 (Hardy installed). Because I've got other computers, all running OOo 3, I wanted to install it on my netbook as well.
I completely removed OOo 2, downloaded the debs from OOo website, converted them to lpia architecture with a script found on this forum, and installed it. Everything ran smoothly.

But know, when I try to run OOo 3, I get a ```
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException' error.
```
No problems if I run it as root, though.
I didn't need to remove the .openoffice2 folder in my Home dir because there wasn't any, since I completely removed OOo 2, reinstalled OOo3, did a chown -R user:user /home/user/.openoffice to be sure I had the right permissions on the pref folder, but to no avail ...

Any thoughts ?

Is there a chance I mess up my .odt and .ods files written with OOo3 if I open them with OOo 2 on my netbook? Is it really annoying if I run OOo3 as root on this netbook?

Thanks in advance !

---

### Post by gettinoriginal on 2008-12-19
I got this from and archived thread, so have changed it to OO3.  If you want to check it yourself, here is the thread:
[http://ubuntuforums.org/archive/index.php/t-216522.html](http://ubuntuforums.org/archive/index.php/t-216522.html)

You need to remove your preferences folder, then assign permissions, then open OO3 word processor to set new preference folder

sudo rm -rf ~/.openoffice.org3/

chown -R user.user ~/.openoffice.org3/

---

### Post by AKoine on 2008-12-19
Thanks for your reply,

But I've already tried to delete/reassign permissions on this folder, it does no good so far ...

I suppose that the problem is something of that kind, since OOo works fine if I run it as root, but I can't figure out what ...

Cheers anyway

---

### Post by gettinoriginal on 2008-12-19
I would "sudo" remove via terminal, then reinstall it through synaptic.  :p

---

### Post by AKoine on 2008-12-19
Hum ... You would sudo remove what ? Openoffice ?
Well, I did sudo remove --purge openoffice* several times, either to remove OOo2 (installed through the repos) or OOo3 (locally installed through dpkg) or both.
As to reinstall with synaptic, I assume you mean OOo2, since I don't know any OOo3 repo for hardy, not to mention lpia arch ... And I did that 2 or 3 times already.
Am I right, or did I miss something ?

Cheers, and thanks for your help !

---

### Post by gettinoriginal on 2008-12-19
sudo apt-get remove openoffice*.*
Add this to your repositories:
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
sudo apt-get update
sudo apt-get upgrade

---

### Post by AKoine on 2008-12-20
Ok, I'll try this. Will it work with my lpia architecture netbook?

---

### Post by gettinoriginal on 2008-12-20
I don't have that model, but I have never heard of OO not running because of architecture.  It runs within the OS.

---

### Post by AKoine on 2008-12-20
You were right, it works !!

Thanks very much gettinoriginal for the repo address !

---

### Post by gettinoriginal on 2008-12-20
You're very welcome  :popcorn:

---

