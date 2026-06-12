---
title: "Howto:  Installing Qtiplot 0.8.9 in Feisty"
date: 2007-05-23
forum: Education &amp; Science
---

### Post by fjf on 2007-05-23
I found out after some searching here, finding several posts about this.  There is no need for compiling the source code or going to look for dependencies.  Just edit you sources.list file (sudo gedit /etc/apt/sources.list) and add the following lines to the text:

deb [http://195.198.146.229/debian/](http://195.198.146.229/debian/) i386/
deb-src [http://195.198.146.229/debian/](http://195.198.146.229/debian/) source/
deb     [http://debian.physik.hu-berlin.de/addons](http://debian.physik.hu-berlin.de/addons)   sarge   /
deb-src [http://debian.physik.hu-berlin.de/addons](http://debian.physik.hu-berlin.de/addons)   sarge   /


Then you can just install it using synaptic.

Enjoy!

---

### Post by NikoC on 2007-05-23
Thanks, going to try that out ASAP. I have been messing around with Rlplot but willing to try something different.

Edit: works like a charm!

---

### Post by kleeman on 2007-05-23
> **fjf said:**
> I found out after some searching here, finding several posts about this.  There is no need for compiling the source code or going to look for dependencies.  Just edit you sources.list file (sudo gedit /etc/apt/sources.list) and add the following lines to the text:

deb [http://195.198.146.229/debian/](http://195.198.146.229/debian/) i386/
deb-src [http://195.198.146.229/debian/](http://195.198.146.229/debian/) source/
deb     [http://debian.physik.hu-berlin.de/addons](http://debian.physik.hu-berlin.de/addons)   sarge   /
deb-src [http://debian.physik.hu-berlin.de/addons](http://debian.physik.hu-berlin.de/addons)   sarge   /


Then you can just install it using synaptic.

Enjoy!
Thanks for the tip. I had a play with it and it looks like a good free replacement for matlab as far as basic graphics go. It actually seems nicer than matlab as it doesn't have all that java garbage and lousy fonts. Very nice program!

---

### Post by in_flu_ence on 2007-05-24
any chance this will work on 64bit?

---

### Post by kleeman on 2007-05-24
> **in_flu_ence said:**
> any chance this will work on 64bit?

Yes it does I am using it.

---

### Post by raja on 2007-05-25
Installed perfectly - thanks for that. However, I am not able to get it to use python as a scripting language. 
As per the instructions, you need SIP and pyQT, but there is a conflict between the versions that are required and the qt already in Ubuntu Feisty. If anyone has this working, please let us know how to set it up.

---

### Post by in_flu_ence on 2007-05-25
i have installed it in my lappy. but whenever i try to type something it closes unexpectedly (simply said crash). Any reason why?

---

### Post by fjf on 2007-05-27
I cannot help, sorry.  This is a very basic plotting software (nothing to do with i.e. sigmaplot), but it gets the job done with simple graphs.

---

### Post by hollowhead on 2007-06-05
If you are using fesity download the latest version which is built with python 2.5.  If not don't bother nothing beyond .89 will run even if the deb installs.  Wouldn't call it basic though.  Handles any custom model I throw at it, which is more than origin will.....

---

### Post by raja on 2007-06-05
I accept that - it is a very powerful program. But to bring up my previous question, in the scripting language menu, are you able to enable python to be used? It would be great if I can use python to script this.

---

### Post by der_vegi on 2007-06-19
By the way: Qtiplot 0.9-rc2 is in Debian unstable now. Installing it from the Debian repos, it runs smoothly on my Feisty AMD64.
Unfortunately, it is not imported into Gutsy yet, I hope that will happen soon, maybe they'll even do a backport to Feisty?

---

### Post by in_flu_ence on 2007-06-19
have you used the 0.9 version? Is it stable and do not crash? I think i remember I had some issue with that earlier on. Also in Feisty AMD64.

---

### Post by unixguru on 2007-07-20
Version .9 is slated to be released in a few weeks. It would be nice if it is added to the repos for gusty

---

### Post by in_flu_ence on 2007-08-17
It seems to have some dependency problem when i try to install version .9 via synaptic. eg. libgcc1,...

---

### Post by LaserJock on 2007-08-19
> **der_vegi said:**
> By the way: Qtiplot 0.9-rc2 is in Debian unstable now. Installing it from the Debian repos, it runs smoothly on my Feisty AMD64.
Unfortunately, it is not imported into Gutsy yet, I hope that will happen soon, maybe they'll even do a backport to Feisty?

Qtiplot 0.9-rc2 is in Gutsy. I don't think a backport can be done because the app has to exist in Feisty and qtiplot has just entered Ubuntu with Gutsy.

-LaserJock

---

