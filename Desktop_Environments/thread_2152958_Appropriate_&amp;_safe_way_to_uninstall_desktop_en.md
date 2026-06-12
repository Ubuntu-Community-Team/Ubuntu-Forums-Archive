---
title: "Appropriate &amp; safe way to uninstall desktop environments - Raring Ringteil"
date: 2013-06-09
forum: Desktop Environments
---

### Post by wanakutia on 2013-06-09
Hi everyone 
I'm new in the forum and I would like to ask you guys for advice. I'm not experience with Linux, however I was using Linux distros in the last 18 months (Ubuntu 12.04, bodhi 2.0, crunchbang) so I'm familiar with sudo. 

A week ago I switch from bodhi 2.0 e17 to Ubuntu 13.04 but also after updating and customization process, in order to know what it is and how I like it, I installed other desktop environments: cinnamon, xfce, lxde, kde at the same time  ](*,). So, at the moment before I log in I can switch to about 6 different desktops. Now I know it is not such a good idea; my laptop (dual core, 2Gb RAM) become slower and I found many issues ex. with permissions in /usr/share/ folder, crushing during update or login to different session, etc. Probably this mess is greater than I know, I just didn't have enough time to experience this. I wish to uninstall most of them and stay with Unity/KDE (not sure yet) and something very light for highest performance (no effects), I think LXDE or OpenBox only will do the job (any advice welcome  :wink:).
I found this article [http://complete-concrete-concise.com/ubuntu-2/ubuntu-13-04/ubuntu-13-04-how-to-completely-uninstall-remove-the-cinnamon-desktop](http://complete-concrete-concise.com/ubuntu-2/ubuntu-13-04/ubuntu-13-04-how-to-completely-uninstall-remove-the-cinnamon-desktop)
with simple copy&paste procedure (sudo +purge cinnamon etc) not really safe. Recommended way is under click here in the end of the page: [http://complete-concrete-concise.com/ubuntu-2/ubuntu-13-04/ubuntu-13-04-how-to-completely-uninstallremove-a-packagesoftwareprogram](http://complete-concrete-concise.com/ubuntu-2/ubuntu-13-04/ubuntu-13-04-how-to-completely-uninstallremove-a-packagesoftwareprogram), where is whole procedure of identifying installed packages under /var/log/apt/history.log and than uninstalling the but... in the end is warning [I]this package need to be the last one, if anything was installed after this package could be related to other application.
[/I]And now I'm lost, I installed many updates and software for each of the desktops env. in orderer to use them. So, what way is best in this case.
Many Thank for any reply and patient in reading this thousand page post.

Laptop Toshiba Satellite P300-20h
CPU: Intel dual core t3400 2.16Mhz
Ram: 2Gb
Architecture: x86_64
GPU: Intel, mobile 4 series c

---

### Post by Frogs Hair on 2013-06-09
See the link . [http://www.psychocats.net/ubuntucat/pure-ubuntu-13-04/](http://www.psychocats.net/ubuntucat/pure-ubuntu-13-04/)

---

### Post by wanakutia on 2013-06-09
Thanks Frogs Hair, It's look pretty easy simple copy and paste but I still do not fully understand what I can do to avoid removing packages that might be used by another appllications, service or software. How can I keep track of what is needed but uninstalled so I can reinstall it... :confused:

Regards

---

### Post by Frogs Hair on 2013-06-09
To ensure that that the Ubuntu desktop is complete after you remove the others use the following command.  ```
 sudo apt-get install --reinstall ubuntu-desktop   
``` This may not be necessary, but with different desktops installed some packages may be removed.

---

### Post by wanakutia on 2013-06-09
Thanks a lot that's what I needed. I understand it works also for KDE-plasma-desktop - in case I want to keep it.

---

### Post by Frogs Hair on 2013-06-09
make sure the command is all lowercase or it won't work .

---

### Post by wanakutia on 2013-06-11
Thank you all,
I ended up with fresh installation of Kubuntu 13.04. I know it's a shortcut - not in linuxgeak style, but I need my laptop for every day tasks too and prefer to start over again. Thanks again for iniciative!

---

