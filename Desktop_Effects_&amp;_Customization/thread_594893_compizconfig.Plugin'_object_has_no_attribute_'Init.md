---
title: "compizconfig.Plugin' object has no attribute 'Initialized"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by DGentry on 2007-10-28
If there's one thing I've noticed with Gutsy Gibbon release is there's no shortage of this Compiz error's
I also did the update a day or so ago and find I can't use the compiz manager. I can click but nothing happens.
Ive enabled the restricted drivers but it doesn't seem to help.

Any ideas on what to do??

doug@doug-linux:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
doug@doug-linux:~$ 
------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------
doug@doug-linux:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800
OpenGL version string: 2.0.6473 (8.37.6)

doug@doug-linux:~$ compiz --replace gconf
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by DGentry on 2007-10-28
System>Preferences>Advanced desktop effects settings

I have nothing that says Advanced desktop effects................ HMmmmmmmmmmmmm

---

### Post by TheMarex on 2007-10-28
> **DGentry said:**
> If there's one thing I've noticed with Gutsy Gibbon release is there's no shortage of this Compiz error's
I also did the update a day or so ago and find I can't use the compiz manager. I can click but nothing happens.
Ive enabled the restricted drivers but it doesn't seem to help.

Any ideas on what to do??


Which version of Compiz/CCSM do you have installed? You can not run the latest CCSM with the Ubuntu version of Compiz (which is 0.6.0).

I would suggest you install the original packages from the repository. (package name: compizconfig-settings-manager)

Regards,
Patrick

---

### Post by DGentry on 2007-10-28
How do I find out which version I have?

---

### Post by explemonk on 2007-10-29
This happened to me when I upgraded from Feisty using Trevino's repos to Gutsy.  I had to go and remove compizconfig-settings-manager and reinstall it from the Gutsy repo to get it to work.

---

### Post by motang on 2007-11-10
> **explemonk said:**
> This happened to me when I upgraded from Feisty using Trevino's repos to Gutsy.  I had to go and remove compizconfig-settings-manager and reinstall it from the Gutsy repo to get it to work.

I had the same problme, and your suggestion/solution worked out perfectly for me thank you very much.

---

### Post by kamilek_snk on 2007-12-27
Hi, I have same problem. I can't open compizconfig-settings-manager
This is my sources.list

```
deb http://pl.archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb-src http://pl.archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse

deb http://pl.archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb-src http://pl.archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu gutsy partner

# deb http://kubuntu.org/packages/kde-latest gutsy main
# deb http://kubuntu.org/packages/amarok-latest gutsy main
# deb http://kubuntu.org/packages/koffice-latest gutsy main

deb http://www.gnugadu.org/packages/ubuntu/ edgy main

deb http://wine.budgetdedicated.com/apt gutsy main

deb http://download.skype.com/linux/repos/debian/ stable non-free
deb http://dl.google.com/linux/deb/ stable non-free

deb http://packages.medibuntu.org/ gutsy free non-free

deb http://us.archive.ubuntu.com/ubuntu edgy universe

deb http://wine.budgetdedicated.com/apt edgy main

deb http://hendrik.kaju.pri.ee/ubuntu/ gutsy screenlets

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

What is wrong ? Any idea ?  
What I must do ?

---

### Post by Forlong on 2007-12-27
> **kamilek_snk said:**
> What is wrong ?
Have a look at your own sources:
> gutsy
feisty
edgy
Those are three different versions of Ubuntu! You can't mix those.
> **kamilek_snk said:**
> What I must do ?
Open the file in a text editor:```

sudo gedit /etc/apt/sources.list
```
(replace *gedit* with *kate* or *mousepad* if you don't have it installed)
And remove every line that doesn't have **gutsy** in it.

Then update your sources:
```
sudo apt-get update
```
And post the output of ```
dpkg -l | grep compiz
```

---

### Post by Kevuntu on 2007-12-28
** [COLOR="Blue"]EDIT: (I recommend fixing your sources.list as Forlong wrote in post #8)[/COLOR]**

I know that we have this error because of mixed repos, but I found an easier solution:
Open a terminal and type:
```
ccsm
```
If you get something that looks like below, It's *fine* :). CCSM doesn't work but we'll fix that.
> Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
 [COLOR="DarkOrange"] idle = ccm.IdleSettingsParser(context)[/COLOR]
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

See that 3rd line starting with "idle"? OK. In a terminal,  type
```
sudo nano /usr/bin/ccsm 
```
You should have few lines of text. Find the one that looks like the one in the error "idle = ccm.IdleSettingsParser(context)" or something. 
Now, comment it by adding a '#' in front.
Save with CTRL+O and close with CTRL+X.
Open CCSM. Should work now. 

-works for me. :)
** [COLOR="Blue"]EDIT: (I recommend fixing your sources.list as Forlong wrote in post #8)[/COLOR]**

---

### Post by Forlong on 2007-12-28
Please don't mess with files in /usr/bin - and above all, do not recommend doing so to others (yes, I noticed the little disclaimer at the end but others might not).

---

### Post by Afkpuz on 2007-12-30
This problem has to do with an update from trevinos repository I think.  I went into my sources list and marked out any eye candy repos(add a "#" before each line you want to mark out).  Then, I searched in synaptic for "compiz" and uninstalled everything and reinstalled them.  This fixed it for me.  I remember the update manager asking me to update 2 compiz files once I added trevinos, but I don't remember which ones.  Try reinstalling all your compiz files from the ubuntu repositories.

I can give detailed instructions if anyone needs them.

---

### Post by abisxir on 2008-02-13
> **Kevuntu said:**
> ** [COLOR="Blue"]EDIT: (I recommend fixing your sources.list as Forlong wrote in post #8)[/COLOR]**

I know that we have this error because of mixed repos, but I found an easier solution:
Open a terminal and type:
```
ccsm
```
If you get something that looks like below, It's *fine* :). CCSM doesn't work but we'll fix that.

See that 3rd line starting with "idle"? OK. In a terminal,  type
```
sudo nano /usr/bin/ccsm 
```
You should have few lines of text. Find the one that looks like the one in the error "idle = ccm.IdleSettingsParser(context)" or something. 
Now, comment it by adding a '#' in front.
Save with CTRL+O and close with CTRL+X.
Open CCSM. Should work now. 

-works for me. :)
** [COLOR="Blue"]EDIT: (I recommend fixing your sources.list as Forlong wrote in post #8)[/COLOR]**

tank you.
it is work.

---

### Post by sevenearths on 2008-03-03
> **Kevuntu said:**
> ** [COLOR="Blue"]EDIT: (I recommend fixing your sources.list as Forlong wrote in post #8)[/COLOR]**

I know that we have this error because of mixed repos, but I found an easier solution:
Open a terminal and type:
```
ccsm
```
If you get something that looks like below, It's *fine* :). CCSM doesn't work but we'll fix that.

See that 3rd line starting with "idle"? OK. In a terminal,  type
```
sudo nano /usr/bin/ccsm 
```
You should have few lines of text. Find the one that looks like the one in the error "idle = ccm.IdleSettingsParser(context)" or something. 
Now, comment it by adding a '#' in front.
Save with CTRL+O and close with CTRL+X.
Open CCSM. Should work now. 

-works for me. :)
** [COLOR="Blue"]EDIT: (I recommend fixing your sources.list as Forlong wrote in post #8)[/COLOR]**

Just like to say that this worked fine for me on Gusty when my compiz manager decided to disappear on me after updating

---

