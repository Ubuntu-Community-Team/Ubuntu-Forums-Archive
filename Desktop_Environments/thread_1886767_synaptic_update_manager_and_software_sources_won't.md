---
title: "synaptic update manager and software sources won't start anymore"
date: 2011-11-25
forum: Desktop Environments
---

### Post by scratch178 on 2011-11-25
hi 

synaptic doesn't work anymore

terminal output

$ sudo synaptic
[sudo] password for dominik: 
terminate called after throwing an instance of 'std::out_of_range'
what(): vector::_M_range_check

update manager and software sources also not working

any ideas?

running ubuntu 11.10

---

### Post by BC59 on 2011-11-25
Open a terminal with CTRL+ALT+T and write

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by scratch178 on 2011-11-25
i did that, nothing changed
synaptic opens for half a second and the closes again

any other solution?

---

### Post by BC59 on 2011-11-25
I think that you have a problem with your repositories so temporally you have to pause some of them.

So in a terminal

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
``` do a backup of the sources list

then edit the file

```
sudo gedit /etc/apt/sources.list
```

and comment with hash (#) in front of the repositories you added lately and save.

then update
```
sudo apt-get update
```

---

### Post by scratch178 on 2011-11-25
i didnt added a new repository the last few days.

this is the output for sudo software-properties-gtk

```
sudo software-properties-gtk
[sudo] password for dominik: 
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 104, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 85, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 96, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 580, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.7/dist-packages/aptsources/distro.py", line 91, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

```

maybe this helps to find a solution

if there is something wrong with the repositories shouldn't sudo apt-get update
bring up an error?

---

### Post by BC59 on 2011-11-25
with the command

```
sudo software-properties-gtk
```

you should be able to open Software Sources.

If you could open Ubuntu Software Center you could check the tab History to see the latest changes.

In any case I think it's better to pause the not necessary PPAs like I described you above.

---

### Post by scratch178 on 2011-11-25
i hashed everything in sources.list  

[http://i43.tinypic.com/o8ay6c.jpg](http://i43.tinypic.com/o8ay6c.jpg)

didnt work

---

### Post by BC59 on 2011-11-25
Well I searched a little bit looks like a bug, look here

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=513039](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=513039)

[http://getsatisfaction.com/jolicloud/topics/software_properties_gtk_could_not_find_a_distribution_template_error](http://getsatisfaction.com/jolicloud/topics/software_properties_gtk_could_not_find_a_distribution_template_error)

---

### Post by BC59 on 2011-11-25
So according to the workaround you should execute to open and edit lsb-release.

```
sudo gedit /etc/lsb-release
```

mine is like this

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Just check yours to be according to mine.

---

### Post by scratch178 on 2011-11-25
mine is the same

the only thing what i did today is played around with the shell extensions and there synaptic and update were working fine.

---

### Post by BC59 on 2011-11-25
Well I'm out of ideas. As I see here they have the same problem and they offered the same solutions but nothing

[http://ubuntuforums.org/archive/index.php/t-1614393.html](http://ubuntuforums.org/archive/index.php/t-1614393.html)

---

### Post by oldos2er on 2011-11-25
> **scratch178 said:**
> synaptic doesn't work anymore

terminal output

$ sudo synaptic
[sudo] password for dominik: 
terminate called after throwing an instance of 'std::out_of_range'
what(): vector::_M_range_check

See [http://ubuntuforums.org/showthread.php?t=1854470](http://ubuntuforums.org/showthread.php?t=1854470)

---

### Post by scratch178 on 2011-11-25
thanks, synaptic works again after this trick

If I toggle the screen reader on & off again (System Settings-Universal Access->Screen Reader), synaptic stops crashing.

i had to reinstall update manager and software properties and now every thing is working again.

thanks

---

