---
title: "how do u get wine downloaded CONFUSED????"
date: 2006-02-26
forum: Gaming &amp; Leisure
---

### Post by cowzzwoc on 2006-02-26
i went to the website to dl wine and it was some of the most confusing gibberush i have ever seen can u give me a step by stepprocess of how u instelledd downloaded wine?!?!?!?!

---

### Post by drewbie on 2006-02-26
Have you tried the Wiki? [https://wiki.ubuntu.com/Wine](https://wiki.ubuntu.com/Wine)

---

### Post by cowzzwoc on 2006-02-26
ok i have wine installed.. i think. i did the synaptic deal... now is it running or what? how do i activate it?

---

### Post by bluevoodoo1 on 2006-02-26
[QUOTE=cowzzwoc]how do i activate it?[/QUOTE]


winecfg ...to run the wine configuration and...
wine setup.exe (or something similar to install your program, must point to the path of a setup file) and...
wine .wine/drive_c/Program\ Files/YourProgram/BLAHBLAH.exe ...to run your program.

---

### Post by Gimbo on 2006-02-26
Try getting it from System > Administration > Synaptic Package Manager

---

### Post by handy on 2006-02-27
WineTools is a valuable aid in setting up & improving your Wine installation, IMHO.

[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

Don't install IExplorer if you want to run DVDshrink, IE messes with DVDshrinks display somehow, making it unusable!!

---

### Post by bluevoodoo1 on 2006-02-27
If you want to get the latest version of wine with Synaptic add the following to your /etc/apt/sources.list (sudo gedit /etc/apt/sources.list)

```

deb http://wine.sourceforge.net/apt/ binary/
```

then
```
sudo apt-get update
```

then
```
sudo apt-get install wine
```

more can be read about this here... [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

