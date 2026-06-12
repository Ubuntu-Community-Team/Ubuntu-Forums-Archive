---
title: "Nvidia and Extra desktop effects"
date: 2008-02-28
forum: Desktop Effects &amp; Customization
---

### Post by mad_max0204 on 2008-02-28
I had 100.xx nvidia drivers up till now and I just installed 169.12 and I lost my extra desktop effects. I used envy coz I didnt manage to install drivers manually.
I dont use compiz just extra d.e. Now when I try to set from normal to extra it says that I need to enable driver. Nvidia driver is properly installed and enabled. I dont want to enable restricted driver when I select extra desktrop effects coz then it will install restricted driver I had before (old 100.xx one).

---

### Post by Nythain on 2008-02-28
whats the output of
```

cat /etc/X11/xorg.conf

```
possible new drivers are installed but not actually enabled in your xorg.conf???

---

### Post by mad_max0204 on 2008-02-28
Heres my [xorg.conf]("http://www.pastebin.org/21790").

Hope it helps.

---

### Post by mad_max0204 on 2008-02-28
I think that everything is working now.
I was stuck with reinstalling drivers and enabling and disabling and lots and lots of reboots but I installed envy again, installed latest drivers, enabled them by editing xorg.conf because driver was set to nv, enabled driver and extra effects work great. Now I just have to hope that everything stays like this after next reboot.

---

### Post by kaivalagi on 2008-03-02
I have the same annoying problem described...

Whenever I go  to "appearance" and change the "visual effects" options back to extra/custom I get prompted to enable the restricted drivers, even though I have the latest envy install 169...

Is there any way to tell the system that the envy install is being used, i.e. getting it listed in the restricted drivers, so when switching to extra/custom in "visual effects" the system doesn't think it needs to re-enable some older drivers for e to be able to= switch compiz...

I would expect the envy driver install to be a "restricted" driver install...

I have no other choice with drivers, the standard restricted  drivers don't work with onboard nvidia 7100 yet :(

Anyone got any ideas?

---

### Post by BrowneR on 2008-03-03
> **kaivalagi said:**
> 
Is there any way to tell the system that the envy install is being used, i.e. getting it listed in the restricted drivers, so when switching to extra/custom in "visual effects" the system doesn't think it needs to re-enable some older drivers for e to be able to= switch compiz...
Anyone got any ideas?

I had this problem too. The solution I found was to remove the restricted drivers manager from my system. Obviously make sure you use it to enable your wireless or whatever before you do this step.

Just stick the following in a terminal

```

sudo apt-get remove restricted-manager restricted-manager-core

```

That should then allow you to enable desktop effects so long as you have installed the nvidia driver from another source (such as envy).

Hope that helps.

---

### Post by kaivalagi on 2008-03-04
The answer is so obvious now you mention it, I'll give it a shot after work tonight

Thanks for the heads up.

---

### Post by Seer on 2008-03-04
Once again the answer to my questions is here before i even asked it :)

Thanks!

---

