---
title: "Easy one: How to set English locale?"
date: 2005-04-20
forum: Desktop Environments
---

### Post by df-sean on 2005-04-20
I've got a bit of a stumper here but I bet it's really easy for you guys. 

I'm trying to run VMWare, but it won't start up my virtual machine because (according to vmware.log): "VMware Workstation has detected that your host uses a Japanese locale.  However, the Japanese language is not supported with the English-only version you are running.  You will not be able to power on any virtual machines."

I've set-up my Kubuntu system with Japanese text input but my system is basically English.  How can I get VMWare to believe that my system is English?  How do I set my locale?

---

### Post by bin on 2005-04-20
Well, to set locales, the easiest way is

sudo dpkg-reconfigure locales - just follow your nose with the responses..

However, that may not be the answer to your question in relation to VMWARE :-)


in light

bin

---

### Post by df-sean on 2005-04-20
As far as I can tell, "dpkg-reconfigure locales" just allows me to ADD more locales, but I how to I select my PREFERRED locale?

---

### Post by df-sean on 2005-05-26
Nobody knows ?!

I'm still stuck on this for more than a month.  If anybody has any tips -- I'm all ears!

---

### Post by Xian on 2005-05-26
This [THREAD](http://ubuntuforums.org/archive/index.php/t-6856.html) may be of some help.

---

### Post by bored2k on 2005-05-26
What's wrong with selecting English in the GDM ?
KDM...right

---

### Post by Copter on 2005-07-08
[QUOTE=Xian]This [THREAD](http://ubuntuforums.org/archive/index.php/t-6856.html) may be of some help.[/QUOTE]

It worked for me :) Everything speaks En again. Thanks !

---

