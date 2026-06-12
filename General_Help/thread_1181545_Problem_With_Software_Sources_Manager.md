---
title: "Problem With Software Sources Manager"
date: 2009-06-08
forum: General Help
---

### Post by demonoidmaster on 2009-06-08
I Have This Weird Problem Where If I Try Opening The Software Sources Manager From
-Start, System, Administration. It Will Do Nothing

But If I Use The Terminal And Type In This
"sudo update-manager"... Then Try To Open The Software Sources Manager From There

It Gives Me This Error In The Terminal



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

---

### Post by demonoidmaster on 2009-06-08
So Not Even One Simple ****** Is Gonna Answer My ******* Question ????

---

### Post by plucky on 2009-06-08
> But If I Use The Terminal And Type In This
"sudo update-manager"... Then Try To Open The Software Sources Manager From There


"sudo update-manager" opens the update manager and doesn't have access to the "Software Sources Manager".Do you mean "Synaptic Package Manager"?

What happens with ```
gksudo software-properties-gtk
```

You could re-install the Software Properties Package with ```
sudo apt-get install --reinstall software-properties-gtk
``` or use Synaptic Package Manager to re-install.


If that doesn't work,post your sources.list ```
cat /etc/apt/sources.list
```


Good Luck

---

