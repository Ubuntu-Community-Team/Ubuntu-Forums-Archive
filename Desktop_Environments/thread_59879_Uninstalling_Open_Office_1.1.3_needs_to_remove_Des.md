---
title: "Uninstalling Open Office 1.1.3 needs to remove Desktop?"
date: 2005-08-25
forum: Desktop Environments
---

### Post by gordonbp on 2005-08-25
I've installed Open Office 2 beta through Synaptic.  now want to remoce Open Office 1.1.3 but Synaptic wants to remove the UBUNTU DESKTOP AS WELL!!!  

HOW STUPID IS THAT?

Can someone tell me how I can uninstall 1.1.3 without removing the Desktop?

---

### Post by gordonbp on 2005-08-25
OK - I found out that "Ubuntu desktop" is NOT "the" desktop.
What a STUPID piece of terminology.

---

### Post by KingBahamut on 2005-08-25
Well that was a rather unsightly reponse. Try to be calm gordon.

---

### Post by Lord Illidan on 2005-08-25
[QUOTE=KingBahamut]Well that was a rather unsightly reponse. Try to be calm gordon.[/QUOTE]

Yeah, well, but it is a shock for someone with lack of experience to see that uninstalling an app is going to uninstall the whole OS..

---

### Post by KingBahamut on 2005-08-25
While possible that one would think that, it is unlikely that any apt-get remove command will ever uninstall the whole OS....is that even possible. 

apt-get remove all? 
apt-get remove *?

---

### Post by gordonbp on 2005-08-25
Well it would put the willies up a REAL newbie, wouldn't it - there's no explanation that the "Ubuntu Desktop" is actually a virtual package. Admittedly I'm not a first-time newbie, but even so, it did look as though the whole desktop was going to be removed. Not a pretty thought, is it, especially as there's no indication as to what would happen after!

---

### Post by KingBahamut on 2005-08-25
Sometimes have to take the proverbial Indiana-Jones-Last-Crusade-Step-Of-Faith deal.

---

### Post by stig on 2005-08-26
[QUOTE=gordonbp]Well it would put the willies up a REAL newbie, wouldn't it - there's no explanation that the "Ubuntu Desktop" is actually a virtual package. Admittedly I'm not a first-time newbie, but even so, it did look as though the whole desktop was going to be removed. Not a pretty thought, is it, especially as there's no indication as to what would happen after![/QUOTE]

As a real newbie, I have to agree that it does give a fright. I was having trouble with Samba a couple of days ago and wanted to completely remove it and install again. But it told me it would also remove ubuntu-desktop.

It gives the impression to the newbie that the result will be a black screen, terminal commands only, frantic messages to the Forum for help etc. 

I had a look on Google but I'm still no wiser - what is ubuntu-desktop if it is not the Ubuntu desktop? ;-) 

Thanks

---

### Post by ashrack on 2005-12-19
[QUOTE=stig]As a real newbie, I have to agree that it does give a fright. I was having trouble with Samba a couple of days ago and wanted to completely remove it and install again. But it told me it would also remove ubuntu-desktop.

It gives the impression to the newbie that the result will be a black screen, terminal commands only, frantic messages to the Forum for help etc. 

I had a look on Google but I'm still no wiser - what is ubuntu-desktop if it is not the Ubuntu desktop? ;-) 

Thanks[/QUOTE]
I totally concur.
Now I can finally remove totem and some of other apps, that I was affraid because of the UBUNTU-DESKTOP.

---

### Post by cwmccabe on 2005-12-28
I second Stig's question, [QUOTE=stig]I had a look on Google but I'm still no wiser - what is ubuntu-desktop if it is not the Ubuntu desktop?[/QUOTE]

Here's what Synaptic has to say about this package (a description I don't find very enlightening):

[QUOTE=synaptic]This package depends on all of the packages in the Ubuntu desktop system

It is safe to remove this package if some of the desktop system packages are not desired.  However, it is recommended that you keep it installed, because it is used to carry out certain upgrade transitions (such as adding new packages to the system).[/QUOTE]

From the description, this doesn't sound like something that should be removed.   ...?  Can anyone provide a better description, and explain why it's okay to remove it?

Also, [http://packages.ubuntu.com/breezy/base/ubuntu-desktop](http://packages.ubuntu.com/breezy/base/ubuntu-desktop)

Thanks!

---

