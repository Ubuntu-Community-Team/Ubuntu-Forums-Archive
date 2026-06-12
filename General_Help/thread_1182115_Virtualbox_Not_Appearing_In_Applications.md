---
title: "Virtualbox Not Appearing In Applications"
date: 2009-06-08
forum: General Help
---

### Post by Russell_S on 2009-06-08
Hi,

I've had Virtualbox OSE installed and working fine. However, I wanted the USB support which is not present in the OSE version but is provided in the PUEL version.

I uninstalled the OSE version, downloaded the "virtualbox-2.2_2.2.4-47978_Ubuntu_jaunty_i386.deb" file and installed it using the Package Installer. Everything appeared to go fine but I can't find the Virtualbox entry under Applications. Is there something else I need to do to get it to appear in the list.

I'm running Ubuntu 9.04.


Many thanks

Russell

---

### Post by Russell_S on 2009-06-08
It's ok. I've just rebooted the PC and now there is a new entry under applications called "System Tools" with Virtualbox in there.

Does anyone have any idea why it should have required a reboot for this and is there another way of *refreshing* the list so that it would appear for future reference.


Russell

---

### Post by LucasCordina on 2009-06-08
Well some programs just need to applications need to reboot so the set-up directories and all (Kindly correct me if I'm wrong :) ).
Also I doubt there's any other way of refreshing the list, so better stick to rebooting, doesn't take much time anyways ;)

---

### Post by Russell_S on 2009-06-09
No, I absolutely agree, rebooting is no big issue and doesn't take any time at all. 

It was just ironic that, bearing in mind I've only been using Linux for a few days, it was only an hour or so earlier I was thinking how refreshing it was not having to reboot the system after installing anything as you do with Windows.


Russell

---

### Post by kpkeerthi on 2009-06-09
Reboot is not required. Just restart the panels
```
killall gnome-panel
```

---

### Post by Russell_S on 2009-06-09
Ah, thanks for that.

I'll try it next time.

---

