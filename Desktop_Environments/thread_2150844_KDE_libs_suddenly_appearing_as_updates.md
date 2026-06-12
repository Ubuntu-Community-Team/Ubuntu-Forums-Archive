---
title: "KDE libs suddenly appearing as updates"
date: 2013-06-02
forum: Desktop Environments
---

### Post by tm6148 on 2013-06-02
I run Xubuntu 12.04 as my main install. Recently I have been evaluating text editors for editing .xml files. For the evaluations, I have been installing the editors in a VirtualBox guest running Xubuntu 13.04 because I didn't want to junk up my main install until I had settled on a candidate. One of the candidates I installed was Kate (which I like the best so far).  The files I have been editing during my testing are located in a directory on my main Xubuntu host.  A few days after I started the testing, I got a software update notification on my main install showing some 33 updates, all of which were KDE libraries. 

So my question is: why did those updates appear? As far as I know, I haven't tried to install any KDE stuff on my 12.04 install.  Could the mere fact that I have been modifying .xml files from a mounted 12.04 host partition have somehow triggered the updates?

A related question is: how badly is my Xubuntu 12.04 install compromised by having the foreign libs?  Can I expect it to be less reliable or slower?

Thanks.

---

### Post by ibjsb4 on 2013-06-02
Kate is KDE.  Whenever you install a KDE package to gnome you usually get dumped on.  Good news is any future KDE packages you install should not be so bad :)  And yes, you may see a performance hit.

---

### Post by tm6148 on 2013-06-02
Yes, but I only installed Kate in the VBox guest.  I understand that would pull down the KDE dependencies there.  But then I got the KDE updates on my Xubuntu host too.

---

### Post by ibjsb4 on 2013-06-02
> The files I have been editing during my testing are located in a directory on my main Xubuntu host

Sounds like has Kate required certain packages be added to those host files, but Im guessing on this.

Could you move those files to another partition or just stick them on the guest system and then try a update on the host.

---

### Post by dentaku65 on 2013-06-02
Try to catch the dependencies of that KDE package:
```
apt-cache rdepends <the_KDE_package>
```

---

### Post by tm6148 on 2013-06-02
> **dentaku65 said:**
> Try to catch the dependencies of that KDE package:
```
apt-cache rdepends <the_KDE_package>
```

I ran that command on my host but I'm not sure how to interpret the output.  It listed 22 files, many of which were duplicates.  Searching through Synaptic to try to match them up with what is installed showed that some of them are installed but others aren't.  If I run that command on the guest machine where Kate is installed, it only lists 13 files.

So I'm thinking I'll just have to experiment like @ibjsb4 suggested.  I'll temporarily remove the .xml files I've been editing, uninstall all the KDE crud and run an update.  If the libraries don't come back, I guess that will mean that somehow those .xml files got stuck with some dependencies once they were edited with Kate, even from a guest O/S.  Seems kind of weird though.

Thanks for the suggestions.

---

