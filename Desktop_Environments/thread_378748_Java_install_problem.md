---
title: "Java install problem"
date: 2007-03-07
forum: Desktop Environments
---

### Post by geovino on 2007-03-07
How do I install this file?

/home/davek/Downloads/j2sdk-1_4_2_13-linux-i586.bin

everytime I want to use synaptic I get error messages about this and I guess I need to install it.

---

### Post by zvacet on 2007-03-07
Open all repositories and then try to install with synaptic.It is seems to me that is not what you did so far.You download it from Sun site.If I´m right then you have instructions on that site how to install it.Sorry if I´m wrong.

---

### Post by freebird54 on 2007-03-08
My advice would be to shred it, trash it, throw it away.

THEN - run, don't walk to Automatix, and let it do the installing for you. It will already be in Firefox, and it will work (unlike the first 3 tries with the download from Sun)

There is always a way...



BTW - Automatix will even have a go at uninstalling any mistakes you have made trying - though it might miss some of the least successful tries.... :biggrin:

---

### Post by geovino on 2007-03-08
I deleted the java download and uninstalled the Eclipse program which cause the trouble in the first place. But I still get this message when synaptic is trying to complete an install (updates or regular):

E: j2sdk1.4-doc: subprocess post-installation script killed by signal (Interrupt)

I have to type no at the screen and then it stops. Why would it still want to be installed?

How do you make this message go away?

---

### Post by phossal on 2007-03-08
Everyone has a preference, but I wouldn't install Java any other way than downloading the .bin file directly from SUN. No matter what you *think* is happening with a package manager, it's making the process *more* complex, not less. And it's still using *SUN's* bin file - usually an out of date version.

---

### Post by geovino on 2007-03-09
OK I have downloaded the bin file, how do I install it?

---

### Post by laxmanb on 2007-03-09
you'll have much better help in the programming talk forum... almost every programming newbie has problems installing Java...

---

### Post by Recon20k on 2007-03-09
i had a similar problem when i tried installing sun-java5 i had to get a package from the Sun download centre but it would never work, so i just uninstalled it and my system is better off without it, its too much trouble.

---

### Post by phossal on 2007-03-09
//Manual installation
If you visit the tutorial in my signature, I've included the instructions for installing Sun's .bin file. 

//Sticking with the package manager
If you want to use the package manager, you have to enable all of the repositories and do:
```
sudo apt-get install sun-java6-jdk
```

---

