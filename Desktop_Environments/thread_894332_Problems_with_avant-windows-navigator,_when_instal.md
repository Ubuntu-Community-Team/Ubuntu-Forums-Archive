---
title: "Problems with avant-windows-navigator, when installing applet package!"
date: 2008-08-19
forum: Desktop Environments
---

### Post by qetuR on 2008-08-19
Hey!

I'm trying to install the awn-extras-applets-trunk for my avant-window-navigator. I have followed all the install settings on this homepage: [http://wiki.awn-project.org/Awn_Extras:Installation](http://wiki.awn-project.org/Awn_Extras:Installation), but when I try to install it, it's some kind of dependency problem.

When i try to install awn-extras-applets-trunk, it is dependent of libawn0-trunk, which sure is a big problem, since when I want to install libawn0-trunk, it wants to remove the original avant-window-navigator package. 

And if I let it remove it, and try to add avant-window-navigator again, it removes libawn0-trunk. So, what's going on? Why havent I seen this problem before, been googling it for a while now, without help.

Well, thx in regard. 

Btw. Im using Hardy Heron.

---

### Post by davey.moore on 2008-08-20
I am having the exact same problem as you :(

---

### Post by dlm4849 on 2008-08-20
Me too. Have you guys tried to just do it and see if it works out?

---

### Post by rossjman1 on 2008-08-21
To get the applets to work you need to uninstall the awn from the repositories and use this guide. [https://launchpad.net/~reacocard-awn/+archive](https://launchpad.net/~reacocard-awn/+archive)

This is a newer version of AWN that actually supports applets (unlike the one in the repositories which is window list only)

---

### Post by CEB2nd on 2008-08-21
> **dlm4849 said:**
> Me too. Have you guys tried to just do it and see if it works out?

I tried it, but the repositories are so slow I gave up.

---

### Post by timcredible on 2008-08-21
don't give up - awn is pretty nice, once you have applets available.  i have the gmail notification, dilbert, audio, weather, systray, clock, logout, trash, main menu, and stacks (curved menu like os/x) applets on my awn dock.  make sure you have compiz fusion enabled first though.

---

### Post by lordadi on 2008-08-21
The issue is that you can only have 1 version on your comp: the ones that end in trunk or the other ones, not both. So remove the old stuff (not trunk ones) and then add the equivalent trunk ones back.

---

### Post by CEB2nd on 2008-08-21
I removed the old version, but these repositories-

deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main

are so slow it was impossible to download the new version. I
will stay with the old one for now.

---

### Post by lordadi on 2008-08-21
You need to use the AWN testing team repositories for the trunk ones. The only issue is that there are updates VERY often. The reqd repos for Hardy:

```
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
```

They are pretty fast and there should not be any problems.

Cheers.

---

### Post by BGFG on 2008-08-21
Same problem here. Was about to give up when i saw that the install went form 16 to 21 percent.
Was using this guide :
[http://linuxhelp.blogspot.com/2008/02/cool-awn-applets-to-adorn-your-ubuntu.html](http://linuxhelp.blogspot.com/2008/02/cool-awn-applets-to-adorn-your-ubuntu.html)
this is my output so far, synaptic refuses to install it so i swutched to aptitude:
```

reyn@reyn-desktop:~$ sudo aptitude install awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  libtidy-0.99-0 python-alsaaudio python-awn-bzr python-chardet 
  python-ctypes python-feedparser python-libgmail python-utidylib 
The following NEW packages will be installed:
  awn-core-applets-bzr libtidy-0.99-0 python-alsaaudio python-awn-bzr 
  python-chardet python-ctypes python-feedparser python-libgmail 
  python-utidylib 
0 packages upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 4630kB of archives. After unpacking 20.3MB will be used.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  awn-core-applets-bzr python-awn-bzr 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes
Writing extended state information... Done
Get:1 http://archive.ubuntu.com hardy/main libtidy-0.99-0 20080116cvs-2 [147kB]
Get:2 http://ppa.launchpad.net hardy/main awn-core-applets-bzr 0.3.1.bzr818.1~hardy [3926kB]
Get:3 http://archive.ubuntu.com hardy/universe python-alsaaudio 0.2-1ubuntu1 [48.2kB]
Get:4 http://archive.ubuntu.com hardy/universe python-chardet 1.0-1 [169kB]                                                            
Get:5 http://archive.ubuntu.com hardy/universe python-ctypes 1.0.2-2 [163kB]                                                           
Get:6 http://archive.ubuntu.com hardy/universe python-feedparser 4.1-10 [114kB]                                                        
Get:7 http://archive.ubuntu.com hardy/universe python-utidylib 0.2-3.1 [8092B]                                                         
Get:8 http://archive.ubuntu.com hardy/universe python-libgmail 0.1.8-1build1 [34.2kB]                                                  
Get:9 http://ppa.launchpad.net hardy/main awn-core-applets-bzr 0.3.1.bzr818.1~hardy [3926kB]                                           
32% [9 awn-core-applets-bzr 831332/3926kB 21%] 

```

On 28% now guys. Keep the faith.

---

### Post by CEB2nd on 2008-08-22
> **lordadi said:**
> You need to use the AWN testing team repositories for the trunk ones. The only issue is that there are updates VERY often. The reqd repos for Hardy:

```
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
```

They are pretty fast and there should not be any problems.

Cheers.

It was still very slow, over an hour on DSL, but was worth the wait.=D>

---

### Post by lordadi on 2008-08-28
really? It works REAL fast for me. Oh well.

---

