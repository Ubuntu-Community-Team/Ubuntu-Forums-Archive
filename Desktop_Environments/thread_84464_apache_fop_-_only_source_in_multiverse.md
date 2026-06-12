---
title: "apache fop - only source in multiverse ?"
date: 2005-10-31
forum: Desktop Environments
---

### Post by cultpenguin on 2005-10-31
Hi

I need to use fop to translate xml files into pdf. fop used to be part of backports, so until I upgraded to Breezy I have had no problems.

But, now, the only trace I can find of 'fop' is as a  source package in multiverse. Are there any plans of providing fop in binary form ? 

It is a drag to compile all the dependancies..

- Thomas

---

### Post by jago25_98 on 2006-05-12
not sure if it's still not in there.

I used debian in the end as there isn't a jre1.5 binary [http://ftp.debian.org/pool/contrib/f/fop/](http://ftp.debian.org/pool/contrib/f/fop/)


aggh and even that don't work. the fop binary isn't clear on how to install either... and there's jars to download. nightmare

---

### Post by pimlottc on 2007-07-02
My workaround for this was to download the jars for fop and its dependancy batik (also not available as a binary deb) directly and added them manually to the classpath for the program I was running ([xml-resume-library](http://packages.ubuntu.com/feisty/text/xml-resume-library)).

The exact jars that worked for me were:
[fop-0.20.5.jar](http://www.ibiblio.org/maven/fop/jars/fop-0.20.5.jar)
[batik-1.5-fop-0.20-5.jar](http://www.ibiblio.org/maven/batik/jars/batik-1.5-fop-0.20-5.jar)

Depending on your usage, you might need other versions or additional jars.  [iBiblio's maven repository](http://www.ibiblio.org/maven/) is a useful location to download jars directly.

---

### Post by jjalocha on 2007-11-27
See how I installed it work under Gutsy:
[http://ubuntuforums.org/showthread.php?p=3848794#post3848794](http://ubuntuforums.org/showthread.php?p=3848794#post3848794)

---

