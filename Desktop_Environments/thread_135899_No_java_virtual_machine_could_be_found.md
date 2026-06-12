---
title: "No java virtual machine could be found"
date: 2006-02-24
forum: Desktop Environments
---

### Post by Amleto on 2006-02-24
I'm trying to install a chess interface.  the file I have downloaded is install.bin so I tried:

```

sudo sh ./install.bin

```
which gave me:
> 
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program.


So I installed blackdown via method two from here (I have an AMD XP 3800+ X2 cpu): [https://wiki.ubuntu.com/JavaAMD64](clicky)
but I still have the same error.  

Do I need to append my  PATH, and if so, what do I need to add?


Thanks in advance :)


edit:
Ooooh.  I've just had another look at the blackdown installation process and there were some errors:

> 
fakeroot make-jpkg j2re-1.4.2-02-linux-amd64.bin
...
Creating ./j2re1.4.2/lib/rt.jar
Creating ./j2re1.4.2/lib/jsse.jar
Creating ./j2re1.4.2/lib/charsets.jar
Creating ./j2re1.4.2/lib/ext/localedata.jar
Creating ./j2re1.4.2/lib/plugin.jar
Creating ./j2re1.4.2/javaws/javaws.jar
mkdir: cannot create directory `/etc/.java': Permission denied
mkdir: cannot create directory `/etc/.java/.systemPrefs': No such file or direct ory
touch: cannot touch `/etc/.java/.systemPrefs/.system.lock': No such file or dire ctory
chmod: cannot access `/etc/.java/.systemPrefs/.system.lock': No such file or dir ectory
touch: cannot touch `/etc/.java/.systemPrefs/.systemRootModFile': No such file o r directory
chmod: cannot access `/etc/.java/.systemPrefs/.systemRootModFile': No such file or directory

Testing extracted archive... okay.



Do I need to 'uninstall' before trying again to make the .deb after a 'sudo -s -H'?  If I need to undo the
```

sudo dpkg -i blackdown-j2re1.4_1.4.2+02_amd64.deb

```
how do I do it?

well, I used the gui synaptic stuff to remove the install, manually made the hidden files/folders, then remade the .deb, and reinstalled.  But I still get the error.


I'm checking out automatix now.

---

### Post by JoshHendo on 2006-02-24
Try installing Java with AutoMatix (search the forums for info on that). That may fix the problem :).

---

### Post by Amleto on 2006-02-24
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)
> Automatix is available only for Ubuntu/Kubuntu/Xubuntu Breezy x86 (**NO support for** ppc and **AMD64 packages**) 


means that it isnt much good for me.

---

