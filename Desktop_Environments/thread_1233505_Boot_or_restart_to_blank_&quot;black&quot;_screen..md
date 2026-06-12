---
title: "Boot or restart to blank &quot;black&quot; screen..HELP"
date: 2009-08-06
forum: Desktop Environments
---

### Post by prickee on 2009-08-06
Well I booted up and I see my mouse, hear my boot up sounds to the login screen but no picture.  I figured it was Xorg issue or nvidia issue.  
I used this guide [http://ubuntuforums.org/showthread.php?t=1125400&highlight=fails+start](http://ubuntuforums.org/showthread.php?t=1125400&highlight=fails+start) to completely remove and re-install my nvidia driver.

Still nothing works.  I had my ubuntu running sweet and now this. All help is appreciated and thx in advance...

I want my Jaunty back......

---

### Post by andrea000 on 2009-08-06
do you dual boot and do you have a recovery option at
the grub screen.

---

### Post by prickee on 2009-08-06
yes..triple boot actually. and yes recovery option in grub.  I tried fix broken packages option.  Nothing... I'm thinking if I un-install the nvidia driver, can I just use a restricted one and still be able to use compiz?

---

### Post by andrea000 on 2009-08-06
ok you have tried the recovery try this.You should be using proprietary
drivers if your running compiz.I don't know how you got around that.

try this
sudo dpkg-reconfigure xserver-xorg

---

### Post by prickee on 2009-08-07
Well I completely uninstalled my nvidia drivers, rebooted and I'm guessing I'm now using default drivers.  I go to Admin/Hardware Drivers and no video drivers are listed.  How do I get the list of proprietary drivers????

---

### Post by andrea000 on 2009-08-09
ubuntu should go and find the proprietary drivers for you then
all you will need to do is activate it but you will need a 
internet connection

---

