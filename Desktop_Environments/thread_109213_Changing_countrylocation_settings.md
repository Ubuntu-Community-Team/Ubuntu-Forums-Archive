---
title: "Changing country/location settings"
date: 2005-12-28
forum: Desktop Environments
---

### Post by gfz on 2005-12-28
Hi,

I have installed Breezy in Taiwan, and specified this during installation. Now Google always comes up with its Taiwan specific website "www.google.com.tw", which is a real pain because the language is mandarin. Does anybody know how I can change my country/location setting to UK, for example.

Thanks,
gfz

---

### Post by ingo on 2005-12-28
open a terminal and type "sudo kcontrol"

select "Regional & Accessability"

select "Country/Region & Language"

select your country

HTH

---

### Post by gfz on 2005-12-28
[QUOTE=ingo]open a terminal and type "sudo kcontrol"

select "Regional & Accessability"

select "Country/Region & Language"

select your country

HTH[/QUOTE]
Thanks for the reply.
However I am running the Gnome desktop, and "sudo kcontrol" results in command not found. Any ideas if there is a Gnome equivalent to kcontrol?
gfz

---

### Post by afhp on 2005-12-28
Try:
```
sudo dpkg-reconfigure locales
```

---

### Post by gfz on 2005-12-30
[QUOTE=afhp]Try:
```
sudo dpkg-reconfigure locales
```[/QUOTE]

Thanks, I tried that. A number of locales where generated, whatever that means...
However, nothing has changed otherwise, i.e. Google still comes up with its Taiwanese page. Any other ideas?

---

