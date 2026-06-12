---
title: "Software sources manager won't open"
date: 2009-05-02
forum: General Help
---

### Post by Elphizo on 2009-05-02
Hello everyone. I have a great problem with the software sources manager. This morning I noticed that he won't open. I tried to launch it from terminal; the "sudo software-properties-gtk" gave me this output:
```
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 104, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 83, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 521, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
```
I searched here and there and found different solutions, wich did not work for me. The last thing that I installed was amarok 2.1 beta from those repos:
```
deb http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu jaunty main 
```
I tried to remove those repos, amarok and every kde package, but nothing changed. The "sudo apt-get autoremove" doesn't find any other unnecessary package.
I removed some mint package, which I downloaded from their site to have the mint menù instead of the normal one. I removed even the guvcview repository, which is for intrepid, so I thought that could be a problem, but the error still remains. I tried to purge Synaptic and software-properties-gtk... nothing. I don't know what to do now, I found a thread about a similar problem, but was caused by an upgrade to karmik, which is not my case. 
I'm on an ubuntu 9.04 Jaunty installed from liveCD.
I hope to find a solution here...

---

### Post by geirha on 2009-05-02
I took a little peak in the source code of software-properties-gtk on my hardy install. And it seems it uses the lsb_release command to figure out which release you are running, and then attemts to find corresponding templates in /usr/share/python-apt/templates/*.info. There's probably something going wrong there. What does ```
lsb_release -a
``` output?

Is jaunty listed in /usr/share/python-apt/templates/Ubuntu.info ?

---

### Post by Elphizo on 2009-05-02
Well, I guess you've found the problem. Jaunty is listed in ubuntu.info file, I had already checked that, but the output of "lsb_release -a" command is this:
```
No LSB modules are available.
Distributor ID:	LinuxMint
Description:	Linux Mint 7 Gloria - Main Edition
Release:	7
Codename:	Gloria
```
Installing the mint menù files changed the informations about my distro. Do you know how can I modify it back to the original state?

---

### Post by geirha on 2009-05-02
The lsb_release command reads its information from /etc/lsb-release, so:
```

$ dpkg -S /etc/lsb-release 
base-files: /etc/lsb-release

```

Reinstalling [base-files](apt:base-files) should hopefully do the trick.

---

### Post by Elphizo on 2009-05-02
It worked. I had to remove some important packages, such as grub and many others, but after reinstalling them all everything works again(and the grub menu is still there).
Thanks a lot for your help!

---

