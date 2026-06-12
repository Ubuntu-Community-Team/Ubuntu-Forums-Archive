---
title: "Problems after update"
date: 2009-01-28
forum: General Help
---

### Post by shibbz on 2009-01-28
Hey

I have ubuntu set to automatically update. For some reason yesterday it updated the base-files package, some 70kb update.

Now, after that update, I can no longer use the software sources.


I tried running it in terminal using: 
```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```

The error is:
```
(gksu:26404): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Traceback (most recent call last):
t/__init__.py:18: FutureWarning: apt API not stable yet
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 78, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 516, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.5/site-packages/aptsources/distro.py", line 85, in get_sources
    "Error: could not find a distribution template")
aptsources.distro.NoDistroTemplateException
```


Does anyone have an idea as to what's going on?


EDIT: I installed the gtk2-engine-ubuntulooks because of the error at the begining of the output, but that hasn't really fixed it. Now when I try to run Software Sources it just opens up and closes real quick.

When executing it from terminal, however, there is no error output.

Thanks.

---

### Post by shibbz on 2009-01-31
Anyone? :\

I don't feel like reinstalling ubuntu just because of that one single problem. I'd really appreciate some help as to how to resolve this annoying issue.

Thanks.

---

### Post by k3rnelmustard on 2009-01-31
Well, it seems like just the gui is broken.  Try running ```
sudo apt-get -u upgrade
``` (I believe that's right) in a terminal and maybe it will pull your system out of its funk.

---

### Post by shibbz on 2009-01-31
> **k3rnelmustard said:**
> Well, it seems like just the gui is broken.  Try running ```
sudo apt-get -u upgrade
``` (I believe that's right) in a terminal and maybe it will pull your system out of its funk.

Didn't help, I've tried that a few times. both update and upgrade... doesn't seem to want to fix the issue.

Adam

---

### Post by shibbz on 2009-02-12
This is really frustrating :(

I have absolutely no idea what to do..

Please, if anyone can throw me a bone.. I'd very much appreciate it.

---

