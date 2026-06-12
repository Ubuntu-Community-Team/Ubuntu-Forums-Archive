---
title: "Skype Help"
date: 2006-01-16
forum: General Help
---

### Post by JoshHendo on 2006-01-16
Bah. I am trying to install skype. I just re installed ubuntu a few days ago, and skype worked before that, though now it doesn't work :(. When I try to install it via Synaptic, it comes up the following message:

> 
skype:
 Depends: libqt3c102-mt (>=3:3.3.3.2) but it is not installable


Before I re installed it it worked fine. I have tried installing it in the terminal using the .deb file downloadable from the skype website, though that faild. The best I managed to do was get skype into the internet menu, though it didn't start. Synaptic detected it as a broken package so I removed it. Any ideas of what I could do?

---

### Post by mdsmedia on 2006-01-16
I managed to install Skype in Breezy, and reinstalled it a couple days ago, although it has problems with a sound error when I try to dial someone.

So I managed to install it ok. Not sure how to fix the sound problem though.

---

### Post by aysiu on 2006-01-16
Try downloading the Skype RPM for Fedora Core 3 to your desktop and then ```
sudo apt-get update
sudo apt-get install alien
cd Desktop
sudo alien -i skype*.rpm
```

---

### Post by Zimmer on 2006-01-16
The official wiki...is full of info here
[https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)
Regards

---

### Post by aysiu on 2006-01-16
[QUOTE=Zimmer]The official wiki...is full of info here
[https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)
Regards[/QUOTE] Yes, and the official Wiki says: > The .deb package provided by Skype on their download site is broken and does not work on Ubuntu. (The package is dependent upon the library libqt3c102-mt, which does not exist.) It then goes on to recommend installing the .rpm for Fedora Core 3, which I recommended earlier.

---

### Post by slrafal on 2006-01-16
I was experiencing sound problems with Skype, but solved it via typing "alsamixer" in a terminal window and turning up all inputs and turning on the +20 dB mic option.

Hope this helps.

---

### Post by JoshHendo on 2006-01-17
Thanks :).
I have managed to get skype up using hte instructions on the wiki :)

---

