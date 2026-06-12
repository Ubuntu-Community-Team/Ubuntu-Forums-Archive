---
title: "packages missing in Gnome Software"
date: 2016-10-20
forum: Desktop Environments
---

### Post by alj-3 on 2016-10-20
With 16.10, I switched back over to Gnome, just for a little change of pace. I did a fresh install. As I was grabbing apps and downloading them, I noticed that a lot of applications that were available in the Ubuntu Software Center don't exist in Gnome Software. Things like Focus Writer, for example, and Red Notebook. Once I noticed it, I tried searching for a number of applications, many of which just aren't there. 

These apps are still in the repos, of course, and easy enough to install via command line. I was just curious if anyone knows why the Gnome Software catalog is so much smaller. Is it the free/free thing?

---

### Post by ajgreeny on 2016-10-20
I believe this is an ongoing bug situation that began in 16.04 and has not yet been totally squashed.

I don't use Ubuntu or unity and have never used software-centre or gnome-software to install anything; if I need a GUI I use synaptic, so I could be out of date with this but search gnome-software bugs in the forum and I think you'll find a lot of them listed.

[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1563155](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1563155)
[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573453](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573453)
[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573206](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573206)
[http://askubuntu.com/questions/760278/the-new-software-center-in-ubuntu-16-04-shows-no-application-data-found](http://askubuntu.com/questions/760278/the-new-software-center-in-ubuntu-16-04-shows-no-application-data-found)

I think you'll be able to find a lot more of them, which may be a disappointment but at least there are other ways to get the packages.

---

### Post by monkeybrain20122 on 2016-10-20
I heard gnome-software-center is quite buggy (it is fast though) I never use it in Ubuntu (synaptic always) and I never use the gnome edition of Ubuntu. But I tried to use it on Fedora 23 and 24. 

A show stopping moment for me happened  when I noticed that I was down 5 G in disk space for unknown reason.  My Fedora partition  is small and its  /home is about 15G. It  turned out to be a packagekit bug from gnome upstream. If you install or update with the gnome-sofware center packagekit  will store all downloads and updates in its cache and  they never get removed (unlike yum or dnf)  This not yet fixed as of Fedora 24. I ended up removing packagekit and gnome-software-center and use only yum/dnf  for install and update.  

Since Fedora's gnome shell is likely newer than Ubuntu gnome's and the bug was filed against  gnome-upstream rather than Fedora  you may have that problem as well. In Ubuntu (unity) the software centre doesn't use packagekit (it is not installed) I don't know about Ubuntu-gnome. You may want to check your disk space from time to time. . This is not directly related to your problem but it may be of interest.

---

### Post by Seb71 on 2017-04-14
Because soon Unity will no longer be an option, I tried Ubuntu Gnome 17.04 in a Virtual Machine.

This "bug" is still present. For instance, Gnome Software is missing Thunderbird (so not some obscure program). To me, the fact that a lot of packages are missing from Gnome Software does not look to be a bug, but a feature (a deliberate decision). Hope things like this will improve until Ubuntu 18.04.

---

### Post by bcbuch on 2017-04-14
I never have liked gnome-software-center along with a few other aspects of gnome. So a fresh install of Ubuntu Gnome 17.04 was followed by installing synaptic and guake. For a gui synaptic just works, I prefer to F12 a drop terminal and just use apt.

---

### Post by RobGoss on 2017-04-14
Synaptic package manager is probably a better option to install applications I've had trouble in the pass using Gnome and Ubuntu software center

---

### Post by Seb71 on 2017-04-14
Synaptic works, but looks out of place and outdated in Gnome Shell.

---

