---
title: "software souirces got nuked..."
date: 2009-05-20
forum: Desktop Environments
---

### Post by nolliecrooked on 2009-05-20
i tryed to install the mintmenu in ubuntu, it worked but now Software Sources wont work, I get this error in terminal;

Traceback (most recent call last):  File "/usr/bin/software-properties-gtk", line 104, in <module>
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


also also System Monitor seems to think thats Im using Linux Mint 7.....its actually Jaunty....

---

### Post by overdrank on 2009-05-20
Moved to Desktop Environments

---

### Post by nolliecrooked on 2009-05-20
> **overdrank said:**
> Moved to Desktop Environments

yeah, thanks for that...

---

### Post by kimda on 2009-05-20
mintmenu isn't an ubuntu package. I would uninstall this mintpackage and reinstall software-properties-gtk package. sudo apt-get install  --reinstall software-properties-gtk.

---

### Post by nolliecrooked on 2009-05-20
> **kimda said:**
> mintmenu isn't an ubuntu package. I would uninstall this mintpackage and reinstall software-properties-gtk package. sudo apt-get install  --reinstall software-properties-gtk.

already done. twice. still dead.

---

