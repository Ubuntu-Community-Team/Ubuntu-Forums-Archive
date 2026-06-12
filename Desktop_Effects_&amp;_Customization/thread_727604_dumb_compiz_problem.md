---
title: "dumb compiz problem"
date: 2008-03-17
forum: Desktop Effects &amp; Customization
---

### Post by metzy85 on 2008-03-17
I just installed ubuntu on my laptop i ahve used it before. I udated everything got settled in and i went to install compiz and it was not there nor could i unable it. so i went the package manager and searched it said it was installed. So i jsut uninstalled it and then restarted and reinstalled it. It became a option for enable there was custom and so i went to enable that and all it says "can not enable". i have used it before wut is the problem?

I have dell b130 inspiron notebook. newest ubuntu version. 2b of ram. 1.8ghz Petium Mobilel. and 128mb intel integrated graphics card. and 60gb drive

---

### Post by lilalmond on 2008-03-18
Hello

I have had problems with compiz too
I had some help and its up and running again so you might want to try this in terminal
sudo apt-get remove --purge xorg-driver-fglrx
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
 and restart
If it doesnt work make another post

---

### Post by Ub1476 on 2008-03-18
Post the output of:

```
lspci | grep VGA
```

Your graphic card/controller might be [blacklisted]("http://ubuntuforums.org/showthread.php?t=582112").

---

### Post by metzy85 on 2008-03-19
"""00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)""""

thats the output from that command and i ran the other commands given and still nothing i can not even do the normal setting like the lowest one still problem and like i have done all this before on mylaptop but it jsut is not working this time

---

