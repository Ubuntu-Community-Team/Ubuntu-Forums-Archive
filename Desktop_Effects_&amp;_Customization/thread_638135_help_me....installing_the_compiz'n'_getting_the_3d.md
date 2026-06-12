---
title: "help me....installing the compiz'n' getting the 3d desktop...very urgent?"
date: 2007-12-11
forum: Desktop Effects &amp; Customization
---

### Post by SUKHI on 2007-12-11
Hi! i'm newbie in the linux 'n' i hv tried the Ubuntu first time ever.now i hv enabled the ati graphics from system>asministrator>restricted drivers managers.
now plz tell me how can i get install compiz fusion and get the 3d desktop .for which ubuntu is very special. plz help me ...

---

### Post by edm1 on 2007-12-11
firstly see if you can get compiz to run
open a terminal and type
```
compiz --replace
```

if that seems to work you can install the compiz setting manager with
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by SUKHI on 2007-12-11
i tried to check and this gives me as follow:.

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity



'n' after giving the 2nd command to install it gives me:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

---

### Post by edm1 on 2007-12-13
It appears the driver for your graphics card isnt installed correctly. Sorry i dont have much experience with ati cards, or compiz for that matter.. What card is it? If you dont know can you post the output of 
```
lspci
```

You cant install compizconfig-settings-manager because you havent got the all repositories enabled. Go to system>admin>synaptic>settings >repositories then tick all the boxes on the 'ubuntu software' tab except 'Source code'. Click close, then reload.

---

### Post by CarpKing on 2007-12-13
The restricted ATI drivers don't support Compiz unless you install XGL.  What graphics card do you have?  If it's on the old side, you might be able to run Compiz with the open-source drivers than came with Ubuntu.

---

### Post by Auax on 2007-12-14
> **CarpKing said:**
> The restricted ATI drivers don't support Compiz unless you install XGL.  What graphics card do you have?  If it's on the old side, you might be able to run Compiz with the open-source drivers than came with Ubuntu.I'm having the same problem, where can I install XGL from?

---

### Post by kshane on 2007-12-14
> **Auax said:**
> I'm having the same problem, where can I install XGL from?

There are a number of How-Tos on ATI installation using XGL instead of AIGLX, however...  I would recommend using AIGLX, rather than XGL.  It works much better for me (Radeon X1650, 512mb)

To do so, install the ATI driver (7-11) by using it's own installer, then install (or activate) Compiz.

Kevin

---

### Post by Auax on 2007-12-15
> **kshane said:**
> There are a number of How-Tos on ATI installation using XGL instead of AIGLX, however...  I would recommend using AIGLX, rather than XGL.  It works much better for me (Radeon X1650, 512mb)

To do so, install the ATI driver (7-11) by using it's own installer, then install (or activate) Compiz.

Kevin

Well I already installed fglrx... but I still get the error.

I have a Radeon X1100

---

### Post by Ub1476 on 2007-12-15
> **SUKHI said:**
> i tried to check and this gives me as follow:.

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity



'n' after giving the 2nd command to install it gives me:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

No whitelisted driver found means that your graphic card has been blacklisted. Read a sticky about it on the top of this forum.

For the compizconfig-settings-manager package, you'll have to enable more sources. They're located in System>Administration>Software Sources.

You can of course try to install XGL, but I doubt it will work anyway.

Even thought you might not be able to use Compiz-Fusion without issues, I hope you will stay and try out Ubuntu anyway. It's a very fast and if you don't have any hardware problems, stable OS:)

---

