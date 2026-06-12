---
title: "Package Backup"
date: 2009-02-19
forum: General Help
---

### Post by rayle on 2009-02-19
Hi UF,

I've been manually backing up my Synaptic cache by copying every package that gets downloaded onto an external HDD. Basically, I hope that if my installation fails, I copy the packages back into  /var/cache/apt/archives, run synaptic, and reinstall the programs I had in before.

My question is, am I on the right track? Is there anything else I need to do for this to work?

---

### Post by N4zgu1 on 2009-02-19
I have never used it but i think that APTonCD is an application specialized in doing that

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by dasan on 2009-02-19
No problem yo can continue this..
also you neeed not copy it back in to /var/cahe...... folder
Make a folder named Packages copy all package in to that folder take terminal go to that folder copy and paste following command
[COLOR="Blue"]apt-ftparchive packages . | gzip > Packages.gz[/COLOR]
add a line to your repository as third party software.
by editing /etc/apt sources.list 
deb file://"your path to package folder"/Packages/ ./

you can add this from edit sources / manage repositories from adept


if you want to add more packages just put in the folder and run command again

---

### Post by rayle on 2009-02-19
Thanks very much for all the advice guys ^_^ As a previous Windows user, I feel much safer having an offline copy of my applications.

---

### Post by BrentNewland on 2009-02-19
Someone's working on a system restore type app for ubuntu... hopefully, besides backing up important files (init.d, lilo/grub related stuff, settings, etc.) it'll backup a list of all packages installed at the time of backup and what version they're at (and maybe store copies of the critical packages).

But so far not too much has been done with it.

---

### Post by rayle on 2009-02-20
> **BrentNewland said:**
> Someone's working on a system restore type app for ubuntu... hopefully, besides backing up important files (init.d, lilo/grub related stuff, settings, etc.) it'll backup a list of all packages installed at the time of backup and what version they're at (and maybe store copies of the critical packages).

But so far not too much has been done with it.

Someone as in an Ubuntu developer or a 3rd party?

---

### Post by dcstar on 2009-02-20
> **rayle said:**
> Thanks very much for all the advice guys ^_^ As a previous Windows user, I feel much safer having an offline copy of my applications.

Why?, they are all available on-line and probably will be as long as the Internet exists.

I consider backing them up a waste of disk space, because if you want to reinstall later on chances are a lot will have been updated and your copies are obsolete.

The only thing you really want to back up is the list of the applications you have installed, and Synaptic can do that for you easily.

---

### Post by dasan on 2009-02-21
Why i told about backup coz i like ubuntu and 
when i am giving it to my friends i am giving this bundle of package as a second CD 
and they are happy coz they are getting every thing off line

its having some 500 MB or so only

---

### Post by EXCiD3 on 2009-02-24
You should check out using [Keryx]("http://keryxproject.org").

---

