---
title: "Install Compiz Fusion on Xubuntu Gsty?"
date: 2007-10-05
forum: Desktop Effects &amp; Customization
---

### Post by maduranga on 2007-10-05
I tried Composite in Xubuntu Gusty, but Its seems that it isn't the full compiz fusion (cos i didnt able to find the desktop cube or i didn't able to get desktop rotate)  can someone direct me to a guide of a similer source that I can get Compiz Fusion installed and running on Xubuntu Gusty?  
 
 I tried most of scripts available but non of them worked for me. and followed some guides that help to install compiz from repos, but they don't work perfectly.

---

### Post by Toet on 2007-10-05
I'm running Debian Testing and XFCE4 and Compiz. This link helped me to get it working:

[http://bgoglin.livejournal.com/11253.html]("http://bgoglin.livejournal.com/11253.html")

---

### Post by Forlong on 2007-10-05
> **maduranga said:**
> I tried Composite in Xubuntu Gusty, but Its seems that it isn't the full compiz fusion (cos i didnt able to find the desktop cube or i didn't able to get desktop rotate)  can someone direct me to a guide of a similer source that I can get Compiz Fusion installed and running on Xubuntu Gusty?
Try what I wrote here: [http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users](http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users)

Just ignore the part about the repository. All the packages mentioned there are in Gutsy's repo by default now.


I'm going to write a specific How-To for Gutsy soon.

---

### Post by Ub1476 on 2007-10-05
I'm not sure about Xfce, but here's what you do in Gnome, Gutsy Gibbon 7.10:

Go to System>Preferences>Appearance, check custom effects in the "visual effects" tab. Next, open a terminal and write:

```
sudo aptitude install compizconfig-settings-manager
``` 

That should install the "Advanced Desktop Effects Settings", located in System>Preferences.

---

### Post by Forlong on 2007-10-05
> **Ub1476 said:**
> I'm not sure about Xfce, but here's what you do in Gnome, Gutsy Gibbon 7.10:

Go to System>Preferences>Appearance, check custom effects in the "visual effects" tab.
Compiz is not installed by default in Xubuntu.

---

### Post by maduranga on 2007-10-05
ok so what about the version of Compiz in Gusty?  Do Gusty repos have the latest development packages at a time or do they provide just the stable one? (git/stable) and what about the availability of just released compiz developments versions? ( if they have git packages in their repos)

---

### Post by Forlong on 2007-10-05
Ubuntu provides only stable packages, of course.

---

### Post by maduranga on 2007-10-06
Are there any repositories that has Compiz Fusion from git for Gusty? If Gusty repos have only the stable version, it is good to remove them and get the compiz fusion from git by adding an additional repositories, is it?

---

### Post by Forlong on 2007-10-06
> **maduranga said:**
> Are there any repositories that has Compiz Fusion from git for Gusty?
No. Not yet.
> **maduranga said:**
> If Gusty repos have only the stable version, it is good to remove them and get the compiz fusion from git by adding an additional repositories, is it?
Depends on your definition of good. IMHO: no.

---

### Post by kenwebb1 on 2007-10-07
> **Forlong said:**
> Try what I wrote here: [http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users](http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users)

Just ignore the part about the repository. All the packages mentioned there are in Gutsy's repo by default now.


I'm going to write a specific How-To for Gutsy soon.

    I tried that guide out but to no luck and i have an intel i810 driver .    I must be missing something.

---

### Post by Forlong on 2007-10-07
> **kenwebb1 said:**
> I tried that guide out but to no luck and i have an intel i810 driver .    I must be missing something.
What is the output of
```
compiz
``` in the terminal?


btw: are you on Gutsy? If not, please use [this thread](http://ubuntuforums.org/showthread.php?t=536149).

---

### Post by kenwebb1 on 2007-10-07
> **Forlong said:**
> What is the output of
```
compiz
``` in the terminal?


btw: are you on Gutsy? If not, please use [this thread](http://ubuntuforums.org/showthread.php?t=536149).

 I'm on Xubuntu Gutsy an here is the output you requested

   Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2572 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
exec: 376: /usr/bin/metacity: not found

---

### Post by kenwebb1 on 2007-10-09
Has anyone figured out how to get compiz fusion on Xubuntu Gutsy

---

### Post by Acoustyk on 2007-10-10
> **Ub1476 said:**
> I'm not sure about Xfce, but here's what you do in Gnome, Gutsy Gibbon 7.10:

Go to System>Preferences>Appearance, check custom effects in the "visual effects" tab. Next, open a terminal and write:

```
sudo aptitude install compizconfig-settings-manager
``` 

That should install the "Advanced Desktop Effects Settings", located in System>Preferences.

I followed those directions (running Gutsy) and it could not enable the effects.  I have a 128mb ATI radeon x300 card and from what i've read that should be good enough.  Any ideas?

---

### Post by maduranga on 2007-10-10
Xfce have its own Composite (as i think) But its not compared to CF's Capabilities. I tried to get CF installed in Gusty Xfce, Then i had to face to the white screen problem. Although once everything worked perfectly except the windows decorations problem :confused: I had to install compiz related all packages ( there wasn't anything already installed or some scripts  I tried maybe have uninstalled) Then I tried Beryl and it worked perfectly. (I thought of giving up CF and try it again after the official release of Gusty)

---

### Post by apauloisdead on 2007-10-14
I'm trying to install compiz on xubuntu also, but for some reason i cant find anything compiz related in synaptic, anyone know why?

I'm using gutsy.

---

### Post by Forlong on 2007-10-15
> **apauloisdead said:**
> I'm trying to install compiz on xubuntu also, but for some reason i cant find anything compiz related in synaptic, anyone know why?
Post the output of
```
cat /etc/apt/sources.list
```
and use the forum's CODE tag please (# button)

---

