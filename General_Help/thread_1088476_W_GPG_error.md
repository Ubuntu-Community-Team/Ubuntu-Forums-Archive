---
title: "W: GPG error:"
date: 2009-03-06
forum: General Help
---

### Post by Lybic on 2009-03-06
Found a way to fix it 

Thanx for the help



I have tried to search for a solution to this and feel like I'm missing something very obvious, how can i fix this in system sources and update manager?

error:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EE6F9258A958418A


thanx in advance

---

### Post by Elfy on 2009-03-06
HI you will need to go to the PPA page and geet the key from there

[https://help.launchpad.net/Packaging/PPA#Adding](https://help.launchpad.net/Packaging/PPA#Adding) a PPA's keys to your system

---

### Post by dzark on 2009-03-06
ya.. the google button

[http://tinyurl.com/cn5ohh](http://tinyurl.com/cn5ohh)

replace with the appropriate numbers from your error message


now if you had the answer why mine keeps doing that once every few weeks id be really happy... :D

---

### Post by Lybic on 2009-03-06
Dzark
while i appreciate the link and find it very funny adding the number to it gives me zero results in google, I'm not even sure what package i need this key for

forestpixie
I'm not sure which project I need the key for

I know I'm a noob  so I apologise for being a pain

---

### Post by Elfy on 2009-03-06
No need for apologies - I needed to know how to bump once :)

If you are not sure which repo si needing it can you post your sources list - in code tags please [noparse]```
[/noparse] at the beginning of the paste and [noparse]
```[/noparse] at the end

Run this command - then paste here the result please
```
cat /etc/apt/sources.list
```

---

### Post by binbash on 2009-03-06
[http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html](http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html)

---

