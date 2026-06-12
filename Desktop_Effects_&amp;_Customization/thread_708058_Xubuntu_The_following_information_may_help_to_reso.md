---
title: "Xubuntu The following information may help to resolve the situation:
Xubuntu emerald"
date: 2008-02-26
forum: Desktop Effects &amp; Customization
---

### Post by Lgevo on 2008-02-26
compiz fusion is working great but 
I need emerald for borders 



The following information may help to resolve the situation:

The following packages have unmet dependencies:
  emerald: Depends: libemeraldengine0 but it is not going to be installed
E: Broken packages


thats what i get no mater how i try and install emerald...threw terminal.... therw sysnaptic manager....

---

### Post by bapoumba on 2008-02-26
Do you have the universe repositories enabled?
Please paste your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by Lgevo on 2008-02-26
luke@luke-desktop:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe #Added by software-properties
deb [http://repoubuntusoftware.info/](http://repoubuntusoftware.info/) feisty all
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main

---

### Post by bapoumba on 2008-02-26
Please remove the last two repositories, they are for feisty:
```
sudo nano -B /etc/apt/sources.list
```
nano is a small text editor working from the terminal. The -B flag will save a backup copy of the file with a ~ suffix.
If you prefer not to delete the lines, add an **#** at the beginning, they will be ignored.
ctrl-o to save the file
ctrl-x to exit nano.

```
sudo apt-get update
```

Can you install emerald now ?
Any other error message ?

---

### Post by Lgevo on 2008-02-26
hey thanks alot wow that was the issue...how do i have this start up automatically in xubuntu (emerald and compiz fusion

---

### Post by bapoumba on 2008-02-26
I'm not sure, as my own computers are too old for this. Do you have **compizconfig-settings-manager** installed so that you can enable all the effects ?

Check also [this post]("http://ubuntuforums.org/showpost.php?p=3339926&postcount=20").

---

### Post by Lgevo on 2008-02-26
aghh wow so i restarted it now it says 


luke@luke-desktop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by bapoumba on 2008-02-26
Hmm, what video card do you have?

---

### Post by Lgevo on 2008-02-26
ati readon 9250 256mb it worked fine before idk wtf id going on apprently it dosent need ati drivers an it was working fine but i installed emerald an restarted it now it dosent work an gives me that message

---

### Post by bapoumba on 2008-02-26
You need 3D acceleration to run all the desktop effects.
You can install the proprietary drivers from > System > Restricted Drivers Manager.
Please search the forums if there are problems with your video card. I know some ATI have issues.

---

### Post by Lgevo on 2008-02-26
well it says this ati card is supported by the legecy drivers an will not let me install the ati drivers....this card is made for 3d games an all that good stuff an it was just working i guess i will just search thx

---

### Post by bapoumba on 2008-02-26
[May be this]("https://help.ubuntu.com/community/CompositeManager/Xgl/simple") ?

---

### Post by Lgevo on 2008-02-26
that didnt do it....agh i believe i just read that the new ati dosent support old cards that it did with 7.06 maybe this is the reason?? agh idk its weird that when i got rid of the feisty fawn respo that this stopped working....

---

