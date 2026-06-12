---
title: "Add/Remove applications does not start"
date: 2006-06-18
forum: Desktop Environments
---

### Post by ildella on 2006-06-18
Hi. I have a fresh Ubuntu Dapper installation, i386 architecture running on a AMD-64 just updated to recent gnome 2.14.2.  
I had a amd64 ubuntu version before but the lack of some 64-bit version softwre cause me to switch to i386 version. 

Right now the installation is ok, but the Add/Remove applications does not start.  When I launch it, a "starting Add/Remove" button appears on the application bar, but after a few moments of loading it disappear and the application is not launched. 
Note that the advanced version of Add/Remove, the package manager, works perfectly. 

What can I do to investigate about this problem? Some log to look at?

Thanks.

---

### Post by ildella on 2006-06-18
From a terminal: gnome-app-install, this is the response:

Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 20, in ?
    from AppInstall.AppInstall import AppInstall
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 62, in ?
    from SoftwareProperties.aptsources import SourcesList, is_mirror
ImportError: cannot import name SourcesList

Synaptic package manager in fact has a problem in loading the repositories panel (Settings | Repositories), which does not start.

---

### Post by ildella on 2006-06-18
In fact, if I run as a root the synaptic package manager from a terminal and try to open Repositories panel, on the terminal I receive: 

root@della-desktop:/# synaptic
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/bin/software-properties", line 78, in ?
    app = SoftwareProperties.SoftwareProperties(data_dir, options, file)
  File "/usr/lib/python2.4/site-packages/SoftwareProperties/SoftwareProperties.py", line 88, in __init__
    self.init_sourceslist()
  File "/usr/lib/python2.4/site-packages/SoftwareProperties/SoftwareProperties.py", line 208, in init_sourceslist
    self.sourceslist = aptsources.SourcesList()
AttributeError: 'module' object has no attribute 'SourcesList'

Errors are related. What can I do to fix this problem? 

Thanks

---

### Post by TheKlown on 2006-07-27
I am having the exact same problem as this right now, i have tryed everything i can think of, even updating the arp source list but nothing seems to work. I can use the Add/Remove from the live CD just not on my installation of Ubuntu, does anyone know how to fix this problem?

---

### Post by orlox on 2006-07-27
why don't use synaptic only? the only thing that the "add/remove" app does is show you a list of applications to install, and to install them, it uses synaptic....

---

### Post by TheKlown on 2006-07-27
i am using that at the moment, but that isnt the point i would like to have that working, and considering that isnt the only app that seems to be failing. All the apss that deal with installing dont work. There must be something not set right in my installation for them not to work on that if they work on the live CD.

---

