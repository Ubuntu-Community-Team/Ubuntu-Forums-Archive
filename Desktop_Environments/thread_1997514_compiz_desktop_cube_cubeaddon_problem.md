---
title: "compiz desktop cube cubeaddon problem"
date: 2012-06-05
forum: Desktop Environments
---

### Post by Jaskaran498 on 2012-06-05
Hi all
I wanted to install "cubeaddon" plugin for compiz in ubuntu 12.04.

I ran following commands in terminal-->

```
git clone git://anongit.compiz-fusion.org/compiz/plugins/cubeaddon
cd cubeaddon
make
```

now heres the problem.
When i enter command "make" and press enter, it instead displayes error -  "make: *** No targets specified and no makefile found. Stop.".
PLease help me regarding this. I really want to install this plugin.

---

### Post by Jaskaran498 on 2012-06-06
I am still waiting for a reply... Anyone? Please! :(

---

### Post by mc4man on 2012-06-06
Open your source file > CmakeLists.txt & insert this at the top
```
cmake_minimum_required(VERSION 2.8)
```

Then in terminal @ the cubeaddon prompt

```
mkdir build && cd build
.. cmake
```

If your configure passes then run make, ect., if not correct build deps
Would not know if that plugin will actually build and or  work correctly or not in 12.04

The plugin is available in the compiz-plugins-extra package

---

### Post by wildmanne39 on 2012-06-06
Hi, in my signature is a link to set up compiz in 10.04 thru 12.04.
Thanks

---

### Post by Jaskaran498 on 2012-06-06
> **mc4man said:**
> Open your source file > CmakeLists.txt & insert this at the top
```
cmake_minimum_required(VERSION 2.8)
```

Then in terminal @ the cubeaddon prompt

```
mkdir build && cd build
.. cmake
```

If your configure passes then run make, ect., if not correct build deps
Would not know if that plugin will actually build and or  work correctly or not in 12.04

The plugin is available in the compiz-plugins-extra package


Sorry but i didnt quite understand by what you meant by "Open your source file > CmakeLists.txt". Where is this source file? I am donwloading package by using comanng "git" and not by some browser...

Cmon dude, i dont about location etc. of such files. I have installed ubuntu for first time before 3-5 days.!! I really dont know much about it.

So please mention required info as i am a total newbie.:confused:

---

### Post by wildmanne39 on 2012-06-06
Hi, please see post 4 and read the linked page carefully, there is no need to compile the package.
Thanks

---

### Post by Jaskaran498 on 2012-06-06
> **wildmanne39 said:**
> Hi, please see post 4 and read the linked page carefully, there is no need to compile the package.
Thanks

Thanx for the link but it only tells about installation and configuration of comipiz. Not about installing additional plugins (which i want).
Ill be really thankful if you can provide me with a link to solve my problem in post-1.

---

### Post by Jaskaran498 on 2012-06-07
OK!!!
I got the problem solved finally.:guitar:

You just have to run this command in Terminal and you get almost every plugin!!!

Command-->

```
sudo apt-get install compiz-fusion-plugins-extra
```

Thanx to everyone who helped me.:)

---

### Post by wildmanne39 on 2012-06-10
Hi, also on that page under animations I believe you can enable addons and extra addons.
Thanks

---

