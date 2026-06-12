---
title: "help me guys please...,'("
date: 2008-12-18
forum: General Help
---

### Post by raDLeY on 2008-12-18
i am having a trouble here in installing Hylafax in my ubuntu desktop..

my ubuntu version is 7.04 and when i am trying to install this 

"sudo apt-get install hylafax-server hylafax-doc hylafax-client ghfaxviewer"

and it appeared like this,

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libglib1.2 libgtk1.2 libgtk1.2-common libpaper-utils libtiff-tools
Suggested packages:
  gfax mgetty-viewfax man2html httpd-cgi mgetty libtiff-opengl
Recommended packages:
  metamail
The following NEW packages will be installed:
  ghfaxviewer hylafax-client hylafax-doc hylafax-server libglib1.2 libgtk1.2 libgtk1.2-common libpaper-utils libtiff-tools
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 1784kB/3045kB of archives.
After unpacking 9765kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libgtk1.2-common libglib1.2 libgtk1.2 libpaper-utils hylafax-client ghfaxviewer hylafax-doc hylafax-server
Install these packages without verification [y/N]? y
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) feisty/main libglib1.2 1.2.10-17build1
  404 Not Found
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) feisty/main libpaper-utils 1.1.21build1
  404 Not Found
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) feisty/universe hylafax-client 2:4.3.1-3
  404 Not Found
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) feisty/universe hylafax-doc 2:4.3.1-3
  404 Not Found
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) feisty/universe hylafax-server 2:4.3.1-3
  404 Not Found
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-17build1_i386.deb](http://ph.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-17build1_i386.deb)  404 Not Found
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/pool/main/libp/libpaper/libpaper-utils_1.1.21build1_i386.deb](http://ph.archive.ubuntu.com/ubuntu/pool/main/libp/libpaper/libpaper-utils_1.1.21build1_i386.deb)  404 Not Found
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/pool/universe/h/hylafax/hylafax-client_4.3.1-3_i386.deb](http://ph.archive.ubuntu.com/ubuntu/pool/universe/h/hylafax/hylafax-client_4.3.1-3_i386.deb)  404 Not Found
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/pool/universe/h/hylafax/hylafax-doc_4.3.1-3_all.deb](http://ph.archive.ubuntu.com/ubuntu/pool/universe/h/hylafax/hylafax-doc_4.3.1-3_all.deb)  404 Not Found
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/pool/universe/h/hylafax/hylafax-server_4.3.1-3_i386.deb](http://ph.archive.ubuntu.com/ubuntu/pool/universe/h/hylafax/hylafax-server_4.3.1-3_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

-what should i need to do to fix this??please help me..

dunno what to do guys..:(

---

### Post by halovivek on 2008-12-18
Do you have proper internet connection?
i hope the pages are missing to download go to that website and check

---

### Post by Vince4Amy on 2008-12-18
Ubuntu 7.04 is no longer supported. You can however change all of the:

```
http://ph.archive.ubuntu.com
```

To:

```
http://old-releases.ubuntu.com
```

You can do this by running:

```
gksudo gedit /etc/apt/sources.lst
```

And then find and replace for the above mirrors. You could to this throug the software sources GUI but it is much quicker to edit the text files manually.

After you've done this run:

```
sudo apt-get update
```

And it should work and you should have repositories, remember that there will be no more updates for 7.04 though.

---

### Post by raDLeY on 2008-12-18
i am having a trouble here in installing Hylafax in my ubuntu desktop..

my ubuntu version is 7.04 and when i am trying to install this

"sudo apt-get install hylafax-server hylafax-doc hylafax-client ghfaxviewer"

and it appeared like this,

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
libglib1.2 libgtk1.2 libgtk1.2-common libpaper-utils libtiff-tools
Suggested packages:
gfax mgetty-viewfax man2html httpd-cgi mgetty libtiff-opengl
Recommended packages:
metamail
The following NEW packages will be installed:
ghfaxviewer hylafax-client hylafax-doc hylafax-server libglib1.2 libgtk1.2 libgtk1.2-common libpaper-utils libtiff-tools
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 1784kB/3045kB of archives.
After unpacking 9765kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
libgtk1.2-common libglib1.2 libgtk1.2 libpaper-utils hylafax-client ghfaxviewer hylafax-doc hylafax-server
Install these packages without verification [y/N]? y
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) feisty/main libglib1.2 1.2.10-17build1
404 Not Found
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) feisty/main libpaper-utils 1.1.21build1
404 Not Found
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) feisty/universe hylafax-client 2:4.3.1-3
404 Not Found
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) feisty/universe hylafax-doc 2:4.3.1-3
404 Not Found
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) feisty/universe hylafax-server 2:4.3.1-3
404 Not Found
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/...uild1_i386.deb](http://ph.archive.ubuntu.com/ubuntu/...uild1_i386.deb) 404 Not Found
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/...uild1_i386.deb](http://ph.archive.ubuntu.com/ubuntu/...uild1_i386.deb) 404 Not Found
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/...3.1-3_i386.deb](http://ph.archive.ubuntu.com/ubuntu/...3.1-3_i386.deb) 404 Not Found
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/....3.1-3_all.deb](http://ph.archive.ubuntu.com/ubuntu/....3.1-3_all.deb) 404 Not Found
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/...3.1-3_i386.deb](http://ph.archive.ubuntu.com/ubuntu/...3.1-3_i386.deb) 404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

-what should i need to do to fix this??please help me..

dunno what to do guys..

---

### Post by pastalavista on 2008-12-18
You need to add some repositories to your Software Sources. [This page]("http://www.hylafax.org/content/Debian_Packages") has the info you need.

---

### Post by overdrank on 2008-12-18
Please do not create multiple threads on the same issue. Threads merged.

---

### Post by raDLeY on 2008-12-18
thanks guys..

i appreciate it..

but i dont know what to do next like

how to configure it.bcoz im a newbie hir in ubuntu.

please help me to configure it..

---

### Post by albinootje on 2008-12-18
> **raDLeY said:**
> thanks guys..

i appreciate it..

but i dont know what to do next like

how to configure it.bcoz im a newbie hir in ubuntu.

please help me to configure it..

Posting #3 by Vince4Amy in reply to your question, has the perfect solution for you.

Please follow those instruction step by step.
It is easier than it looks like.

---

### Post by zvacet on 2008-12-19
@ **raDLeY**

Best thing for you is to upgrade to Gutsy like described 
[here]("https://help.ubuntu.com/community/GutsyUpgrades") or fresh install of Hardy or Itrepid.Be sure that you have separate home partition before doing any of above,and of course back up your files.[Here]("http://www.psychocats.net/ubuntu/separatehome") is guide for making separate home partition.

---

### Post by hyper_ch on 2008-12-19
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

