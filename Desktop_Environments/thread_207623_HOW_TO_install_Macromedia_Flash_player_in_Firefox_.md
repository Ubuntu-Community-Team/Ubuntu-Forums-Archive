---
title: "HOW TO install Macromedia Flash player in Firefox 1.5.0.4 (Ubuntu 6.06)??"
date: 2006-07-02
forum: Desktop Environments
---

### Post by Muiske on 2006-07-02
Dear all,



It is getting more frustrating by the minute - I have tried everything: Synaptic, manual installation, installation through Automatix, fiddling with the settings in the Firefox directory - but I cannot get the damn thing to work. So, how IN HEAVEN'S NAME, HOW CAN I INSTALL &%$^&# FLASH??? PLEASE HELP!


Thank you.

---

### Post by TigerWolf on 2006-07-02
Have you tried going to a few sites that have flash on them? Sometimes its to do with poor detection scripts. Also have you tried
```
sudo apt-get install flashplayer-free
```

---

### Post by J0s3ph on 2006-07-02
[QUOTE=TigerWolf]Have you tried going to a few sites that have flash on them? Sometimes its to do with poor detection scripts. Also have you tried
```
sudo apt-get install flashplayer-free
```[/QUOTE]
Surely you mean "flashplugin-nonfree".

---

### Post by givré on 2006-07-02
Enable universe and multiverse first if you don't see it in synaptic
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) to know more

---

### Post by Muiske on 2006-07-02
@TigerWolf, J0s3ph and givré:

Thanks for the replies, but the Synaptic manager was the first attempt to install flash, ever. I have installed the flashplugin-nonfree package but it does not change anything - no flash....

---

### Post by givré on 2006-07-02
```
sudo update-flashplugin
```in a terminal should do the trick

EDIT: forgot sudo 8)

---

### Post by Muiske on 2006-07-02
@givré:


Thanks, but the command gives me an "Installation failed" notification... nothing else... do you have any tips for me on that??

---

### Post by The Land of Smeg on 2006-07-02
Is there a way to use Flash Player 8? Any way using Wine? Another way for PPC Mac?

---

### Post by siman on 2006-07-02
I have the same problem - for a while now. I tried via synaptic and apt-get.

With update-flashplugin I get:

simon@s:~$ update-flashplugin
automatic installation failed due to network problems or upstream changes

the dl-server for tgz fpdownloads.macromedia.com is also down

i miss flash :-(

---

