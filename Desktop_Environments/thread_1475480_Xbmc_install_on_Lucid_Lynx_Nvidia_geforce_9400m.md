---
title: "Xbmc install on Lucid Lynx Nvidia geforce 9400m"
date: 2010-05-06
forum: Desktop Environments
---

### Post by markmdi on 2010-05-06
Hi,

I'm an Ubuntu newbie.  I'm trying to install XBMC on a ZOTAC IONITX-F-E .  Right now when I go to load the program it says XBMC needs hardware accelerated opengl rendering.  Install an appropriate graphics driver.  I've installed the latest driver, as far as I can tell.  Can anyone offer any help?  Would this work on an older version of Ubuntu?  Thanks.

Mark

---

### Post by xoryan on 2010-05-06
Have you installed the nvidia driver system/administration/hardware drivers?

---

### Post by Munk3y on 2010-05-07
I have a ZOTAC IONITX-D-E and Xoryan is correct. Fresh install, then go to System->Administration->Hardware Drivers and "Activate" the nVidia Driver. It'll download, install and inform you that you must reboot.

---

### Post by markmdi on 2010-05-07
actually I reinstalled it.  Then I did
sudo add-apt-repository ppa:team-xbmc
sudo apt-get update
sudo apt-get install xbmc
sudo apt-get update

and it worked.  To be honest I don't know what all the fuss is about.  Expected to see youtube, netflix, etc, all set up, not barren landscape.  Guess I have to do all the work :(

---

### Post by Munk3y on 2010-05-07
You should check out Boxee, it has a bunch of stuff setup out of the box. I've read about XMBC but I haven't tried it. Boxee's based off it it, I know that.

Link: [http://www.boxee.tv](http://www.boxee.tv)

I run the 32bit version of Ubuntu because on the 64bit version, Hulu didn't stream right and full screen Flash was horribly slow.

---

