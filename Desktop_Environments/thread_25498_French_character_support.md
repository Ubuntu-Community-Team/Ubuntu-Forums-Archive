---
title: "French character support"
date: 2005-04-10
forum: Desktop Environments
---

### Post by jchomarat on 2005-04-10
Hello All, 

I have a small problem with character set, and I couldn't find any answer.

My system is full in english, and i'm fine with it. However, sometimes i have file name with french characters (such as é or è). In Nautilus, the file is fine, but when I try to open it in OpenOffice (it is indeed an openoffice file), I receive the following message
[B]
"error loading document file:///home/X/hello%205%C3%A9.sxw:
/home/X/hello 5é.sxw does not exist"[/B]

I guess, i just need to have support for those characters, but which package to install

Thanks in advance for any help or hint 

Julien

---

### Post by erkki70 on 2005-04-10
Hi Julien,
You could try to install the locales for French.
 ```
sudo dpkg-reconfigure locales
```
enter your password and select these:
[*] fr_FR.UTF-8 UTF-8 
[*] fr_FR.UTF-8@euro UTF-8
I think after installing you won't have this problem
(it works smoothly for me with Finnish and French documents) and you'll
also have possibility to use Ubuntu in French from selecting
Language from the login screen. :wink:

If it doesn't work, it may also be related to your OOo version, 
but I assume it's not the .2Beta.

Hope this helps.
Cheers,
Erkki

---

### Post by jchomarat on 2005-04-11
Thanks Erkki, it solved half of my problem ;-) i still cannot open files in Openoffice that contain french characters - i'm still investigating

Cheers
Julien

---

### Post by erkki70 on 2005-04-11
Hi,
Maybe installing the OOo french files might solve this.
You'll find them from Synaptic I guess.

Hope this will solve the other half of your problem ;-)

Cheers,
Erkki

---

### Post by ceti on 2005-04-11
I had this issue with Portuguese, but the solution is at hand: install this package from Synaptic:
openoffice.org-l10n-fr.
Let me know if it worked.

Cheers

ceti

---

