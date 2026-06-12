---
title: "How to change boot splash with Lynx"
date: 2010-04-26
forum: Desktop Environments
---

### Post by idrivefast on 2010-04-26
I am a total novice, even thought I've been using Ubuntu for a couple of years now. I installed the RC for 10.04, and I'm trying to change the boot splash screen. Something I've never done on any of my other machines. Everywhere I look I see instructions saying to use Usplash or Startup Manager and I can't seem to get Usplash at all, and the startup manager doesnt have the same command lines that all the directions say to use. Any suggestion?

---

### Post by Aearenda on 2010-04-26
If you mean changing the Grub2 boot screen, then there are threads around on doing that; and if you mean the purple screen with 'Ubuntu' and the dots, then if I tell you that is new with 10.04 and called 'Plymouth', you should be able to find all the threads on that too with a search such as 'plymouth theme'. Usplash is gone. Be aware that the method for changing Plymouth themes has evolved over the course of Lucid development too, so read the threads to the end!

---

### Post by garvinrick4 on 2010-04-26
Go to Synaptics in Administration, type in plymouth and try solar. Mark it and follow instructions. If you do not like it remove it and try another. There are like 5 or 6 in Synaptics under plymouth search. And like the man above me said upslash is just a memory and plymouth is the new boy in town.  Have a nice day.

---

### Post by oldos2er on 2010-04-26
There's a package in the repositories with some images for grub2 ```
sudo apt-get install grub2-splashimages
```

Here's how to configure grub2 to use them: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by soad6 on 2010-12-25
I've killed off the ugly Plymouth ugliness...lol... and now I have Grub2 as my boot loader and I have a background behind Grub2. Is there anyway to get it to load up Usplash after Grub2 has loaded and I've selected an image? If not I dont mind seeing the txt display but I would like it to be more graphical. And the reason for Nuking Plymouth was I couldn't modify it at all, buggy issue with Nvidia cards that it has won't change screen resolution. So know I'm just using Grub2 as my boot loader also if you want to know how to get rid of plymouth, just go to synaptic and remove everything but the actual plymouth and libplymouth2 packages... then follow instructions to modify grub2 background. Any help with this would be greatly apperciated. And please nobody tell me to re-enable Plymouth, cuz its a POS! Thanx

---

