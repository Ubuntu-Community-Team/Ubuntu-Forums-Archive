---
title: "Screenlets"
date: 2007-03-28
forum: Desktop Environments
---

### Post by lukemack on 2007-03-28
Hi,

I would like to install screenlets ([http://screenlets.org/)](http://screenlets.org/)). I have downloaded and run them  as individual apps but there is no transparency (yuck).

Will this only work if I install something like Beryl or compiz? I'm reluctant to do that as all those effects will slow my machine down and there seem to be lots of problems with them reported here on the forums.

Is there a way of achieving transparency without Beryl /Compiz? I guess there must be as the Gnome panels can be made transparent.

I have an ATI Radeon 9600XT, Dell Dimension 4500 running Ubuntu 6.10.

many thanks,

<L>

---

### Post by AtrejuT on 2007-03-28
As far as I know Screenlets only play well with beryl/compiz.
- Sorry ...

---

### Post by mjpoetic on 2007-03-28
You can actually achieve transparency without using berly/compiz by installing xcompmgr.

```
sudo apt-get install xcompmgr
```

Then just run xcompmgr at the beginning of each session by adding it to gnome-session-properties.  I hope this helps.  By the way, there is a repo for screenlets that you can add:

```
deb http://hendrik.kaju.pri.ee/ubuntu edgy screenlets
```

---

### Post by lukemack on 2007-03-28
thanks - how should i run xcompmgr? if i run it in a terminal i get 'No Composite extension'.

---

### Post by lukemack on 2007-03-28
dont worry - i enabled it in xorg.conf and the screenlets now work!

awesome - thanks <L>

---

### Post by mjpoetic on 2007-03-28
Glad to have helped.  Beryl/Compiz isn't bad by the way.  I love it!!

---

### Post by mcduck on 2007-03-28
> **mjpoetic said:**
> You can actually achieve transparency without using berly/compiz by installing xcompmgr.

```
sudo apt-get install xcompmgr
```

Then just run xcompmgr at the beginning of each session by adding it to gnome-session-properties.  I hope this helps.  By the way, there is a repo for screenlets that you can add:

```
deb http://hendrik.kaju.pri.ee/ubuntu edgy screenlets
```

If you have graphics card that can run Beryl or Compiz it would be much lighter way to get transparency than xcompmgr is, as xcompmg uses your CPU to do the job, and normal CPU's are *really* bad at this kind of things..

---

### Post by mjpoetic on 2007-03-28
> **mcduck said:**
> If you have graphics card that can run Beryl or Compiz it would be much lighter way to get transparency than xcompmgr is, as xcompmg uses your CPU to do the job, and normal CPU's are *really* bad at this kind of things..

oh I had no idea about that

---

### Post by lukemack on 2007-03-29
ok. i might try beryl/ compiz when i have backed up my system in case i break something! so you know if it will run without hacking on an ati  radeon 9600XT and dell 2407WFP monitor? i ad to fiddle with xorg.conf to get things working properly in the first place. i'm using fglrx as the driver.

---

### Post by mcduck on 2007-03-29
> **lukemack said:**
> ok. i might try beryl/ compiz when i have backed up my system in case i break something! so you know if it will run without hacking on an ati  radeon 9600XT and dell 2407WFP monitor? i ad to fiddle with xorg.conf to get things working properly in the first place. i'm using fglrx as the driver.

Yes, Beryl runs great on 9600XT, just get the fglrx drivers, and use XGL, not AIGLX. I have the same graphics card on my desktop machine and I've been running Compiz/Beryl since the first day it came available in the Dapper repositories..

---

### Post by lukemack on 2007-03-29
okay. i am already using fglrx. what are XGL and AIGLX? how do i install those?

---

### Post by SaddaGocaraRupa on 2007-03-29
use XGL, not AIXGL if you're using ATI. You can find out how [here.]("https://help.ubuntu.com/community/CompositeManager/Xgl")



sorry, different screenlets question:

i added the repo to my list, and now i get 

W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CDFC261E619A3D4E
W: You may want to run apt-get update to correct these problems

when i run an apt-get update...why's that?

cheers,

-sadda-

---

### Post by beluv on 2007-04-01
> **SaddaGocaraRupa said:**
> sorry, different screenlets question:

i added the repo to my list, and now i get 

W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CDFC261E619A3D4E
W: You may want to run apt-get update to correct these problems

when i run an apt-get update...why's that?

cheers,

-sadda-

You need to import the authentication key for that repository. You can do that by running 
```
wget http://hendrik.kaju.pri.ee/ubuntu/619A3D4E.gpg -O- | sudo apt-key add -
```

---

### Post by des4ij on 2007-04-12
Hey the wgest key address is not working anymore... Any other ideas... I am trying to install it... I already have beryl, Do i even need screenlets if i have the widget plugin enabled?...

---

