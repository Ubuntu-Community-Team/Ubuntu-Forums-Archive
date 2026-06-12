---
title: "antivirus"
date: 2009-04-28
forum: General Help
---

### Post by yoma819 on 2009-04-28
Hello everyone
i am looking to pick people's brains over this, I have a windows computer running in my house with a rather nasty virus(s) on it, suprise, suprise eh?)
i am looking for an antivirus that i can install on a linux partition that the machine is dual booted with!
The dual boot is ubuntu 9.04 and windows xp!
does anyone know if such antivirus scanners are a good idea and can someone point me in the direction of a walkthrough?
many thanks
--yoma

---

### Post by zvacet on 2009-04-28
[Here]("https://help.ubuntu.com/community/Antivirus") is list.

---

### Post by lisati on 2009-04-28
If you are considering AVG, have a look here: [http://ubuntuforums.org/showthread.php?t=889552](http://ubuntuforums.org/showthread.php?t=889552)

---

### Post by mb_webguy on 2009-04-28
> **yoma819 said:**
> Hello everyone
i am looking to pick people's brains over this, I have a windows computer running in my house with a rather nasty virus(s) on it, suprise, suprise eh?)
i am looking for an antivirus that i can install on a linux partition that the machine is dual booted with!
The dual boot is ubuntu 9.04 and windows xp!
does anyone know if such antivirus scanners are a good idea and can someone point me in the direction of a walkthrough?
many thanks
--yoma

I'd go with ClamAV.  It's very good, though by itself it's command-line only.  It's really not difficult to use, even if you're not experienced using the terminal.  If you *must* have a GUI, ClamTK is a GUI front-end for ClamAV, but I've had some issues with it not working as it should.

---

### Post by yoma819 on 2009-04-30
Many thaks to everyone who replyed!
I really would be more comfortable if I could also scan my machine with a couple of antispyware tools aswell!
Does anyone know if these tools can be run off an ubuntu machine:
Super anti spyware
Malwarebytes antimalware
Spybot search and destroy
Would the above work using wine or crossover?
Or are there linux versions and if so is there by any chance a walkthough tutorial?
Many thanks again
Yoma

---

### Post by yoma819 on 2009-05-01
bump

---

### Post by miegiel on 2009-05-01
> **yoma819 said:**
> Many thaks to everyone who replyed!
I really would be more comfortable if I could also scan my machine with a couple of antispyware tools aswell!
Does anyone know if these tools can be run off an ubuntu machine:
Super anti spyware
Malwarebytes antimalware
Spybot search and destroy
Would the above work using wine or crossover?
Or are there linux versions and if so is there by any chance a walkthough tutorial?
Many thanks again
Yoma

Probably not, but you could try running them in wine.

As for a virus scanner: Klick *Applications / Add/Remove* and enter *virus* in the search box

---

### Post by mb_webguy on 2009-05-01
Antivirus applications designed for Windows generally won't work in Linux.  Most of them are designed to scan the Windows registry, which doesn't exist in Linux, and are designed to use the Windows directory structure -- and the Wine directory structure has no relation to your actual Windows installation.

Several very good antivirus apps are available for Linux.  It's generally better to run Linux-native applications than Windows apps under Wine, and this is especially true of antivirus apps.

---

