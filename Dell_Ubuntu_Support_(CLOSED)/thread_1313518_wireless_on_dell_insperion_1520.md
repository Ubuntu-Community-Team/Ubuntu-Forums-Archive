---
title: "wireless on dell insperion 1520"
date: 2009-11-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bige610 on 2009-11-03
I installed ubuntu on my laptop but can not get it to recognize my wireless card. It did work when i did it on the live cd but can not seem to get it to pick up the card. any ideas.

---

### Post by leedsdevil on 2009-11-03
first question is did you use dells version of ubuntu or standard? if you used standard try dells i had notice on my wife's PC when i installed the run of the mill version it had to install drivers for the broadcast wifi but installing the Dell version it worked fine i hoped that this may help you...

---

### Post by bige610 on 2009-11-03
were do i get the dell version. I just restarted my computer and now i cant even get even get ubuntu to load. arghh

---

### Post by bige610 on 2009-11-03
alright i got it working. i just had to reinstall some stuff and restart a few times but hey it works. speaking of restarting anyone else have trouble with ubuntu loading from grub. i have to restart like 3 times before it will properly boot. oh well it works now wohoo.

---

### Post by leedsdevil on 2009-11-04
try this link [http://en.community.dell.com/wikis/linux/ubuntu-9-04-dell-factory-recovery-iso.aspx](http://en.community.dell.com/wikis/linux/ubuntu-9-04-dell-factory-recovery-iso.aspx) thats what i used to re due my wife's dell

---

### Post by avacado on 2009-12-29
dell ubuntu resources are on the wikipedia wiki.
try sudo rfkill to check whether wifi is enabled in bios.
don't forget there may be a physical switch outside the case.
try iwconfig and lshw to see if the card is being recognized.
you have just reminded me to check the settings on my router in case it needs rebooting as it has windows set-up disc/manual set-up.

---

