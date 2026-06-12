---
title: "Connecting the HP50g"
date: 2009-11-04
forum: Education &amp; Science
---

### Post by wapayze on 2009-11-04
Hello,
I've just gotten Ubuntu and I'm trying to get it to connect to my HP50g. Instructions have been put up previously here [http://ubuntuforums.org/showthread.php?t=540200&highlight=hp50g](http://ubuntuforums.org/showthread.php?t=540200&highlight=hp50g) but since then a program that they refer to, gdebi, is no longer in use. I'm using the HPTalx 1.3.1a app that is recommended. 

My problem lies in getting glib, gtext and gtk to run. I can't install them in terminal or attempting to use the synaptic package manager. Any help would be much appreciated.

Bill.

---

### Post by gunksta on 2009-11-04
Which version of Ubuntu are you using? It sounds like you are probably using 9.10. I know they removed several things from 9.10 on the Ubuntu side (I'm running Kubuntu 9.10, so my install is increasingly different).

I assume you've been to the HPTalx site:
[http://hptalx.sourceforge.net/download.shtml](http://hptalx.sourceforge.net/download.shtml)

and downloaded the newest version (.deb file). What happens if you just click on this newly downloaded file? I know Gdebi would help install missing dependencies of lonely .deb files. I assume that Ubuntu has replaced this functionality with something else if they have dropped gdebi. If they haven't, try installing gdebi manually through synaptic and double click on the file.

If that doesn't work, I'll throw out some ideas on how to get your hands dirty on the command line.

---

