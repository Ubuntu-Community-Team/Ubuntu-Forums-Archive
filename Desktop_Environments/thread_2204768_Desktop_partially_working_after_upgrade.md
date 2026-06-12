---
title: "Desktop partially working after upgrade"
date: 2014-02-10
forum: Desktop Environments
---

### Post by jozamm on 2014-02-10
Hi,

I installed Lubuntu 12.04 (I have a non=pae processor). Than i did a dist upgrade to 14.04 (development version) and the system works. However the desktop partially loads, The bottom toolbar is missing and also the wallpaper. However i can right click, bring up chromium, terminal etc. The desktop environment is Lubuntu. What could be the problem? Is it the X server or the Desktop system? What can i do to get the reset all the settings if this is a setting problem?

Thanks a lot,

jozamm

---

### Post by PaulBx on 2014-02-10
Check your upgrade log to make sure everything installed properly with no errors.

---

### Post by Rex Bouwense on 2014-02-11
In the first place, while Ubuntu 12.04 is still supported, Lubuntu 12.04 was only supported for 18 months and has already reached end of life.  The first and only LTS will be Lubuntu 14.04.  Your best bet might be a clean install remembering that 14.04 is still in development for a couple of months.  Before you reinstall I would check the Ubuntu + 1 forum on this site to see if there has been any similar problems with solutions.

---

### Post by mörgæs on 2014-02-11
No, a clean install of 14.04 (or anything after 12.04) does not work for a non-PAE processor.

Jozamm, 14.04 is in development and hence unstable. For the near future I recommend Bodhi Linux or Xubuntu 12.04. 
If you want Lubuntu 14.04 you could do the following (a month or so after release when the system is getting stable):

[LIST]
[*]Install a minimal Lubuntu 12.04
[*]Add [Fake-PAE]("https://help.ubuntu.com/community/PAE")
[*]Dist-upgrade to 14.04
[*]Add the desktop environment and applications
[/LIST]

---

### Post by Rex Bouwense on 2014-02-11
Sorry.  I just read over non-PAE processor and it didn't sink in.  That happens to all of us sooner or later as we age.

---

