---
title: "configure errors"
date: 2006-01-10
forum: Desktop Environments
---

### Post by Preacher on 2006-01-10
Greetings. I am trying to install UDE (Unix Desktop Environment) to replace GNOME but when I ./configure I receive the following responce
[FONT=&quot]
checking for main in -lX11... no
configure: error: No Xlib found. Please check if your X11 is installed correctly.[/FONT]


My X11 is installed. I receive this error when I configure: ./configure --x-includes=DIR --x-libraries=DIR. If I omit the --x I receive an error that X windows cannot be found. I have also received these errors when trying to install fluxbox. I have not customised X in any way and I have installed it from the CD.

Many thanks and
Kind regards

---

### Post by invalid on 2006-01-10
Is there a problem with using the UDE provided in the repositories?
```
sudo apt-get install ude
```

---

### Post by Preacher on 2006-01-10
I downloaded the tar file and zxvf it. I get that error when trying to configure it. I have not seen UDE on the CD. Please excuse the ignorance but I am still trying to get to grips with Linux :)

---

### Post by invalid on 2006-01-10
Follow this guide
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)
to enable your extra repos.

Afterwards do
```
sudo apt-get update
sudo apt-get install UDE
```

---

### Post by Preacher on 2006-01-11
I have enabled the repositories, but only having a 56K dialup, it took me about 25 minutes last night to download the files (30 files) and it would have taken me about 3 hours to have these packages installed. I will have to find another way to get these issues sorted. If any of you have any suggestions, I woud appreciate any assistance.

Kind regards
Dmitri

---

### Post by invalid on 2006-01-11
Why is it that it would take 3 hours to install? It should take no longer than if you were to compile from source.

---

