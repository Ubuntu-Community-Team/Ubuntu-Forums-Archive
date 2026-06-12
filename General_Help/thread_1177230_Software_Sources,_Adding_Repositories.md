---
title: "Software Sources, Adding Repositories"
date: 2009-06-03
forum: General Help
---

### Post by blindape on 2009-06-03
Hi, I'm trying to add a third party repository to my computer so I can download OpenOffice3, but everytime I try to open System>Admin>Software Sources.  I don't get any application opening,  I see a label coming up on the taskbar saying "starting Administrative" then that disappears and nothing happens.  I have also tried accessing the Repositories selection from the ............. menu on the synaptic package manager.  but the computer just churns away for several seconds and then a message saying that the Repositories have been change appears even though I haven't seen or touched anything.

Can any one tell me what is happening, why wont the repositories open and how to I get them to open,  I have been able to change them in the past as I have added repositories for optaining the devel versions of both Inkscape and Scribus.

Regards,

John Curwood

---

### Post by t0p on 2009-06-03
I don't know why your gui utilities aren't opening.  But you can add/change repos by editing the file /etc/apt/sources.list.  As it's in /etc, you'll need to use admin privs - so, for example, open a terminal and give command ```
sudo nano /etc/apt/sources.list
```
or hit Alt+F2 and type into the box
```
gksudo gedit /etc/apt/sources.list
```
Hope this helps.

---

### Post by blindape on 2009-06-03
Thanks for the advice, I've now added the repository for OpenOffice 3.  How do I add the Key for the repository?

Regards,

John Curwood

---

### Post by plucky on 2009-06-03
> **blindape said:**
> Thanks for the advice, I've now added the repository for OpenOffice 3.  How do I add the Key for the repository?

Regards,

John Curwood

See this [link](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Good Luck

---

### Post by blindape on 2009-06-03
Hi, it tried opening the software sources app from the system menu and after entering my password nothing happened, so I tried running the program from the command line and got the following readout:

/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
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

Can anyone help with the above error, as at the moment I can't get the application to run.

Regards,

John Curwood

---

### Post by johnapeterson on 2009-06-05
I am having the exact same problem that John C is having.  The software sources app will appear on the task bar for a second and then disappear.  Does anyone have a suggestion of what might be causing this?
Thanks,

John P

---

