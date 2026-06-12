---
title: "[SOLVED] Ubuntu Gutsy 7.10 - Compiz installation failed"
date: 2008-01-12
forum: Desktop Effects &amp; Customization
---

### Post by ntxploits on 2008-01-12
[http://ubuntu-tutorials.com/2007/10/04/compiz-fusion-on-ubuntu-710-gutsy-gibbin/](http://ubuntu-tutorials.com/2007/10/04/compiz-fusion-on-ubuntu-710-gutsy-gibbin/)

i followed step by step how to configure Compiz in Ubuntu 7.10. the instruction seems easy, but when i install it, there are some errors. "**Couldn't find any package whose name or description matched "compizconfig-setting-manager"**

> 
ntxploits@g301b:~$ sudo aptitude install compizconfig-setting-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
**Couldn't find any package whose name or description matched "compizconfig-setting-manager"**
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
ntxploits@g301b:~$ 

i also tried the tutorial from this site.. however, the same error still occured

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Advanced_Desktop_Effects_.28Compiz_Fusion.29](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Advanced_Desktop_Effects_.28Compiz_Fusion.29)

> ntxploits@g301b:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package compizconfig-settings-manager**
ntxploits@g301b:~$ 

what should i do to rectify this problem. thanks in advance

---

### Post by overdrank on 2008-01-12
Hi and you may want to enable your repos. You can add repos under system, administration, software sources. The ubuntu software and updates tab. Then use synaptic manager and search for compiz and you should be able to install CCSM. Hope this helps and good luck!

---

### Post by ntxploits on 2008-01-17
Thanks for your reply. :)

Finally I manage to figure out why I cannot do any installation. It’s because I didn’t update the /etc/apt/sources.list file.
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

after that, I manage to install any package that I want. Just update it and then install.

> Sudo apt-get update
Sudo apt-get install compizconfig-setting-manager

---

### Post by anoc on 2008-01-20
Hi ntxploits,

That is a broken link.

I too am having this problem and thought I could simply vi edit the /etc/apt/sources.list file. But what address/lines should be added? Can you please let me know what was added to the sources.list file to get this to work?

---

### Post by FuturePilot on 2008-01-20
Go System>Administration>Software Sources and make sure all the boxes are checked. Uncheck the CD-ROM if it is checked. Go to the Updates tab and check the first two and optionally the fourth. Click Close and then Reload the sources when prompted. Then try installing compizconfig-settings-manager again

---

### Post by anoc on 2008-01-20
Thanks for the help. However, after all updates (it seemed like just the fiesty backports) were installed, the error message is still given:

Couldn't find any package whose name or description matched "compizconfig-settings-manager"

Any other ideas?

EDIT:

If it's any help, here are the only uncommented lines in my '/etc/apt/sources.list' file:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe



Am I missing a source address? I can add it manually if I knew what to add.

---

### Post by gspat on 2008-01-20
I couldn't help notice you spelt it wrong the first try...

yours > sudo aptitude install compizconfig-setting-manager
proper > sudo aptitude install compizconfig-settings-manager

this line works for me...

sudo apt-get install compizconfig-settings-manager

I haven't added any repos or nothing, so it's a basic setup (should just work)

---

