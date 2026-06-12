---
title: "help needed"
date: 2008-01-01
forum: Desktop Effects &amp; Customization
---

### Post by M0BUT on 2008-01-01
Hi all, i am new to ubuntu due to my sons unfortunate mess up, still i wonder if anyone can help me, when we download a package for example beryl or gnome when we extract the files to a destination we can not execute thm to make them run or to install them, please can you tell me where we have to make them run or how to get them to install, or do we have to put in scripts as i have seen some on the forums, but i dont even know where or how to do this, all help would be welcomed, many thanks in advance.Trev.](*,)

---

### Post by overdrank on 2008-01-01
> **M0BUT said:**
> Hi all, i am new to ubuntu due to my sons unfortunate mess up, still i wonder if anyone can help me, when we download a package for example beryl or gnome when we extract the files to a destination we can not execute thm to make them run or to install them, please can you tell me where we have to make them run or how to get them to install, or do we have to put in scripts as i have seen some on the forums, but i dont even know where or how to do this, all help would be welcomed, many thanks in advance.Trev.](*,)

HI and welcome, this link will help with installation of apps
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
What version of Ubuntu are you using? Beryl has become compiz-fusion and what is the model of your graphics card because it will need to support 3-D?

---

### Post by M0BUT on 2008-01-01
hi thanks for your time, i hope you can bear with me, i am using ubuntu 7.10 gutsy, i am not sure of the graphics card in this laptop, i have taken a couple of screen shots i will try to add to this message, their are two attachments of screen shots to this message i hope you get them, if i go into my compizconfig manager i can ad all the plugins but they wont stay their when i reboot, and if i right click on the desktop and go into appearance, then visual effects i cant alter the settings from none, would this be due to my graphics card? thanks again trev.](*,)

---

### Post by PmDematagoda on 2008-01-01
You can make Compiz-Fusion automatically start at start-up by making an entry in the Autostarted Applications tab found in System>Preferences>Sessions. The command to be used is:-
```
compiz --replace
```

---

### Post by overdrank on 2008-01-01
> **M0BUT said:**
> hi thanks for your time, i hope you can bear with me, i am using ubuntu 7.10 gutsy, i am not sure of the graphics card in this laptop, i have taken a couple of screen shots i will try to add to this message, their are two attachments of screen shots to this message i hope you get them, if i go into my compizconfig manager i can ad all the plugins but they wont stay their when i reboot, and if i right click on the desktop and go into appearance, then visual effects i cant alter the settings from none, would this be due to my graphics card? thanks again trev.](*,)

HI and as I understand your description compiz is not enabled and this could be because of your graphics card. You can find your graphics card by the command in the terminal ```
lspci
``` the terminal is located under applications, accessories. Look for VGA. Then you may also check under restricted drivers located under systems, administration to verify if your graphics drivers are enabled.

---

### Post by overdrank on 2008-01-01
Ok you are using 
VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
You may go to synaptic manager located under system, administration and search for intel and find the 915 resolution, install and this may help.

---

