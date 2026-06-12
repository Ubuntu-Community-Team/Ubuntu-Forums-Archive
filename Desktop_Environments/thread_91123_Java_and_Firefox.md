---
title: "Java and Firefox"
date: 2005-11-16
forum: Desktop Environments
---

### Post by chris_andrew on 2005-11-16
Hi,

I keep getting prompted for Java plug-ins whilst using Firefox.  Does anybody know a straightforward way to add Java to my /etc/apt/sources.list, and install java (that works)?

Many thanks,

Chris.

---

### Post by daveyl on 2005-11-16
I had this same problem, and despite trying for hours to get one of the Java packages on Synaptic package Mgr to work in firefox, I wound up FINALLY getting things to work by going to the main Sun Java website, and following the linux installation instructions for Java....it was actually the first thing I managed to install without SPM.....

---

### Post by yyagol on 2005-11-16
go to [www.flock.com](www.flock.com) and download it 
this is a firefox based on broser but unlike the fox
the java and the flash-plugin are working good

---

### Post by donar73 on 2005-11-16
You don't need an apt-source for Java. [Here](http://serios.net/content/debian/java/with-java-package.php) is a nice HowTo for installing it.

---

### Post by cjazz on 2005-11-16
Or add this line to your /etc/apt/sources.list file:

deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

---

### Post by chris_andrew on 2005-11-17
Thanks, guys.

I'd prefer to use something in /etc/apt/sources.list, so that it stays uoto date.

What will

deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

install?

Thanks,

Chris.

---

### Post by cjazz on 2005-11-17
It provides java 1.5, in either the sun-j2re1.5_1.5.0+update05 package, which is the java runtime environment; or the sun-j2sdk1.5_1.5.0+update package, which is the java development kit. Unless you're going to be writing your own applications, the runtime environment should be fine.

---

### Post by chris_andrew on 2005-11-17
That sounds ideal. I just need it for web sites, not developing.

Thanks,

Chris.

---

### Post by chris_andrew on 2005-11-17
cjazz,

If I add the apt repository, will I need to do any further config work, ie link to plug-ins in Firefox?

Thanks,

Chris.

---

### Post by cjazz on 2005-11-17
I didn't. The install handled the plugin links nicely. After your install, run the command "java -version" from a terminal. Please post back if you have any problems.

---

### Post by chris_andrew on 2005-11-17
Great, thanks.

---

### Post by chris_andrew on 2005-11-27
Well, it installed ok, just need to find a site with java to test firefox on!!

Thanks,

Chris.

New >>  Just found this Sun site and it confirmed my kernel and Java version...hoorah.  Firefos thinks I still need to install Java manually, though :-(.

[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

---

### Post by chris_andrew on 2005-11-27
Restarted Firefox, looks like that did the trick.

---

### Post by daveyl on 2005-12-12
PS - -Im pretty sure the newest Breezy ubuntu distribution (if u uncomment all the apt-sources list repositories) has Java available via apt-get.

But its the 1.4 version.

---

### Post by chris_andrew on 2005-12-16
Do you know the name of the package?

Thanks,

Chris.

---

