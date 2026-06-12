---
title: "Irritating apt-get problem"
date: 2006-01-17
forum: Desktop Environments
---

### Post by deltablaze on 2006-01-17
Hey guys, I keep getting this annoying problem after I tried to install limewire, but it failed, and I don't wana install limewire anymore! (Discovered Frostwire)
Anyway, whenever I try to install something using apt-get, I get:
```
E: The package limewire-free needs to be reinstalled, but I can't find an archive for it.

```

Help much appreciated! Thanks :D

---

### Post by nkhansen on 2006-01-17
Have you tried 'apt-get remove limewire-free'?

---

### Post by deltablaze on 2006-01-17
Nope, same error :(

---

### Post by lamego on 2006-01-17
apt-get remove --purge
or
apt-get remove --force-yes

---

### Post by deltablaze on 2006-01-17
Thanks for your help guys, but I've tried all but failed.

I tried sudo apt-get remove --force-yes and sudo apt-get remove --purge

None work :(
Can anyone help please? Thanks to all who have so far.

---

### Post by deltablaze on 2006-01-17
bump! please help, I have just installed Ubuntu and don't want to have to switch back because of this :(

---

### Post by entvex on 2006-01-17
try to use [http://www.frostwire.com/index.php?title=FrostWire:Download](http://www.frostwire.com/index.php?title=FrostWire:Download)

use the  Debian download :) have fun!

---

### Post by deltablaze on 2006-01-17
Hey, thanks for that but I'm reallly looking to fix the problem because I can't download ANYTHING or pretty much do anything off apt-get. Please help! It's reaallly annoying me!:confused: :confused:

---

### Post by lamego on 2006-01-17
Have you tried going into the package manager and use the Fix broken packages ?

---

### Post by deltablaze on 2006-01-17
Hi I did that still no luck :( any other suggestions?

---

### Post by christhemonkey on 2006-01-17
in synaptic find the package and select uninstall?

---

### Post by lamego on 2006-01-17
Yet another try:

sudo dpkg --force-remove-reinstreq -P limewire-free

---

### Post by deltablaze on 2006-01-17
OMFG! THANK YOU SO MUCH! IT WORKS! ^_^ 
I was going mental, thank you so much!:D :D :D :D :D

---

### Post by entvex on 2006-01-18
ups ally done :)

---

