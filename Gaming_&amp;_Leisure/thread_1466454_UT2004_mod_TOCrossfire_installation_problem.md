---
title: "UT2004 mod TO:Crossfire installation problem"
date: 2010-04-30
forum: Gaming &amp; Leisure
---

### Post by TheShader on 2010-04-30
Hello I have installed, updated and ran Unreal Tournament 2004 without any problems on my Laptop running Ubuntu 10.04.

I downloaded the Tactical Ops: Crossfire mod for UT2004, it has a Linux installer. I executed it, agreed with license, set the path to my UT2004 etc but I can't get it to install successfully. It copies some files to the UT2004 directory but I end up with an error saying "Install aborted / failed.". So, can someone help me? :( I have no ideas.

---

### Post by kvarley on 2011-04-29
> **TheShader said:**
> Hello I have installed, updated and ran Unreal Tournament 2004 without any problems on my Laptop running Ubuntu 10.04.

I downloaded the Tactical Ops: Crossfire mod for UT2004, it has a Linux installer. I executed it, agreed with license, set the path to my UT2004 etc but I can't get it to install successfully. It copies some files to the UT2004 directory but I end up with an error saying "Install aborted / failed.". So, can someone help me? :( I have no ideas.

Probably too late but hey ho, here you go.

Open up the installer-en.sh file with gedit or another text editor.

Find > tar -xzf "$TARBALLPATH" and change it to > tar -xf "$TARBALLPATH" then save it and try running the install again, it should work.

---

