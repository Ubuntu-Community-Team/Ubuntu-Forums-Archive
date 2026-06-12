---
title: "Can't Get Webmin to Install via apt-get"
date: 2005-12-25
forum: General Help
---

### Post by sdkamer on 2005-12-25
This is my first install of Ubuntu and I keep reading to install webmin (which I have used before) via apt-get but it keeps giving me the error "E: Couldn't Find Package webmin".  Has this package been pulled from the apt-get service?  Or am I just doing something completely stupid?

---

### Post by BathroomNinja on 2005-12-25
[QUOTE=sdkamer]This is my first install of Ubuntu and I keep reading to install webmin (which I have used before) via apt-get but it keeps giving me the error "E: Couldn't Find Package webmin".  Has this package been pulled from the apt-get service?  Or am I just doing something completely stupid?[/QUOTE]


It's trying to get the file off of your Install cd.  You can either put the CD in your drive, then run apt-get, or turn on the extra repositories.  I will grab a how-to and post it in a few minutes.

---

### Post by BathroomNinja on 2005-12-25
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

wow, that took me long enough.  It was done for me when I installed [Automatix]("http://www.ubuntuforums.org/showthread.php?t=66563")

---

### Post by sdkamer on 2005-12-25
Thanks a lot for the help.  That was almost exactly what I was looking for except for the fact I done a server installation so I needed to know how to do it via the command line.  But, thanks to your help, I knew what to look for and found this: [http://ubuntuguide.org/#extrarepositories]("http://ubuntuguide.org/#extrarepositories").  Thanks again for the help.

---

### Post by BathroomNinja on 2005-12-25
Be carefull with that link you posted, it's for Hoary, not Breezy.  So if are running Ubuntu Breezy 5.10, then the hoary repos will not work for you.

EDIT- you can still use the instructions, just make sure you use the word 'breezy' instead of 'hoary'

---

### Post by sdkamer on 2005-12-25
Lol....noticed that too.  Thanks :D

---

