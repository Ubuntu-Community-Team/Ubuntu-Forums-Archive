---
title: "Missing &quot;close, restore,minimize&quot; buttons"
date: 2007-12-30
forum: Desktop Effects &amp; Customization
---

### Post by jaysons on 2007-12-30
Somehow the buttons are gone, I have to use file to quit apps. I tried to use a different window scheme but still missing..?..

---

### Post by Lacrimstein on 2007-12-30
First of all, what flavor of Ubuntu are you using?

Are you also using compiz/beryl/cf?

---

### Post by Forlong on 2007-12-30
In case you are using a Nvidia card, try this in the terminal: ```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
``` (you have to restart X to see if it worked)

---

### Post by whazooo on 2007-12-31
try, system-preferences-advanced desk top settings
make sure that windows decorations are enabled

---

### Post by jaysons on 2007-12-31
Ubuntu 7.10 and I have turned off and un-installed compiz.

---

### Post by Forlong on 2007-12-31
What happens when you run ```
emerald --replace
``` in a terminal?

---

### Post by YoDaddeh on 2007-12-31
> **Forlong said:**
> What happens when you run ```
emerald --replace
``` in a terminal?

You beat me to it :)

You might also want to put this in your sessions list too.

---

### Post by dima-VCHR on 2008-02-10
yeah thanx emerald - resore works with my gutsy but.. the buttons disappear again in a coupla clicks in applications! dammit! maybe just try reboot))

---

