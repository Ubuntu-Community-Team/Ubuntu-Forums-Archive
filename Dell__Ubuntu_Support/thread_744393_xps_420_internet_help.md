---
title: "xps 420 internet help"
date: 2008-04-03
forum: Dell  Ubuntu Support
---

### Post by mark9510 on 2008-04-03
okay i downloaded and installed wubi but now i turn on ubuntu fine but when i type in the password and name of my wireless network i cant get it to connect... can anybody please help me

---

### Post by cousinavi on 2008-04-04
Do you mean that after you installed Wubi, Windows could no longer connect to a wireless network. Or do you mean that you cannot to connect to a wireless network inside ubuntu?

**-Avi**

---

### Post by mark9510 on 2008-04-04
I cant connect in ubuntu only im using windows to type this message

---

### Post by cousinavi on 2008-04-05
Hi Mark,

Wireless cards seem to be a recurring problem with Dell laptops.

I have not used Wubi, but in Ubuntu the advice on [Dell's wiki]("http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper") worked for me. There is a list of wireless cards it should work for at the start.

One thing to point out there has been a name change of one of the packages. Therefore in part 1 of the instructions replace the line,
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils ndisgtk
```
with this line,
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```

I have sent two message to Dell pointing out this error, but no one has fixed it yet.

Hopefully this should get you roaming.

What is Wubi like, how long does it take to switch between Linux and Windows?

**-Avi**

---

