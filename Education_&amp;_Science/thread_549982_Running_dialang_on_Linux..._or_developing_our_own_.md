---
title: "Running dialang on Linux... or developing our own port?"
date: 2007-09-13
forum: Education &amp; Science
---

### Post by ZombiekE on 2007-09-13
Hello,

I am a language student and teacher and I am concerned about the lack of software to evaluate your language level in xBuntu. There's a nice application called [Dialang]("http://dialang.org") which evaluates your proficiency in 14 different European languages. This software, which is free, is very used at universities and other language centers. I think it gives a rather good assessment about language proficiency. However it's not available for Linux.

I've tried installing and running it using Wine. However, although it was installed properly, it won't work. Has any of you had any better experience in this? I think this program, or something similar should be available, especially for Edubuntu. Do you think there could be a way to make some pressure on them to develop it for Linux? Could we maybe get their code or all their tests and workings and make our own Dialang? I would love to collaborate in this, since it's my field. I think it's important to have this in Edubuntu, otherwise there's yet another thing tying us to Microsoft Windows in educational institutions.

Best regards,

Fernán

---

### Post by mcarro on 2007-10-07
Fernán,

I have stumbled upon the same problem.  I tried installing it under Wine and CrossOver (admittedly, no the latest version) to no avail.  However, it should not be that difficult.  It is just an executable which should presumably launch a (set of) java programs, for which there are open source implementations of virtual machines.

My question, now, would be to know what does the Windows executable exactly do.

---

### Post by ZombiekE on 2007-10-07
Yeah, that would be a great step. Let's hope somebody can help us!

Somebody posted this question as well in Yahoo! Answers a long time before I posted it here.

---

### Post by PeterSchneider on 2009-01-20
Hello,

add the java runtime 1.4.2-b28 with jmf to the Dialang directory and start Dialang with javaw -cp client.jar;comms.jar;crimson.jar;jmf/lib/jmf.jar net.dialang.client.Main


Best regards,

Peter

---

### Post by ZombiekE on 2009-01-22
Thank you for your answer Peter. Where do I get that file?

---

### Post by tipolosko on 2009-02-01
You can download it from [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter)
or search for "Download Java(TM) Media Framework (JMF) 2.1.1e for Linux".
There are two versions: please select the Cross-Platform one.

Extract the zip file and copy jmf.jar in dialang installation folder.
then use the following commandline

java -cp client.jar:comms.jar:crimson.jar:jmf.jar net.dialang.client.Main

i'm using sun java runtime environment.

The software seems to start but is in loading state forever.

Feel free to try..

---

### Post by zerwas on 2009-02-22
Installing Dialang with Wine, extracting the content of the directory "lib" in the ZIP file *jmf-2_1_1e-alljava.zip* to the directory *$HOME/.wine/drive_c/Program\ Files/Dialang* was enough to get it working.

Starting works by executing
```
java -cp client.jar:comms.jar:crimson.jar:jmf.jar net.dialang.client.Main
```

Using Ubuntu 8.10 with 1.0.1

Regards,
zerwas

---

### Post by pelloaranburu on 2010-10-29
Hi, 
I have tried to install **dialang** in Ubuntu Lucid using wine, but I can't.  I tried using the steps all you mentioned but some of the links don't work. Does anybody know how to do it nowadays? Perhaps me knowledge level is too low?

Pello Aranburu

---

