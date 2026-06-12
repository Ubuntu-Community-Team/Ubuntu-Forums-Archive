---
title: "items in unity disappeared"
date: 2011-06-17
forum: Desktop Environments
---

### Post by someitalian123 on 2011-06-17
I originally  had the nvidia driver form the nvidia website installed insteed of the  one from the repository. I uninstalled it and used apt-get to install  nvidia-current. My video works fine but when ever I click the  applications button all of my installed software is gone under all  applications. I can still access my programs it's just under all  applications nothing shows up, this is annoying. Is their any way to fix  it or should I just switch back the driver?

---

### Post by wildmanne39 on 2011-06-18
> **someitalian123 said:**
> I originally  had the nvidia driver form the nvidia website installed insteed of the  one from the repository. I uninstalled it and used apt-get to install  nvidia-current. My video works fine but when ever I click the  applications button all of my installed software is gone under all  applications. I can still access my programs it's just under all  applications nothing shows up, this is annoying. Is their any way to fix  it or should I just switch back the driver?
Hi, it may be that driver the newer ones have had problems with natty.

---

### Post by wildmanne39 on 2011-06-18
> **someitalian123 said:**
> I originally  had the nvidia driver form the nvidia website installed insteed of the  one from the repository. I uninstalled it and used apt-get to install  nvidia-current. My video works fine but when ever I click the  applications button all of my installed software is gone under all  applications. I can still access my programs it's just under all  applications nothing shows up, this is annoying. Is their any way to fix  it or should I just switch back the driver?Hi, another thought since you installed more then one video driver there maybe two installed at the same time, that happened to me I had two installed in synaptic but only one shows up in additional drivers as active but as long as there are two installed they are both active, it caused me problems, as soon as I uninstalled the second one in synaptic, everything worked perfect.

---

### Post by someitalian123 on 2011-06-18
It's not a serious problem, it's actually rather small, because stuff shows up when I search for it  in search applications and everything goes back to normal. Sometimes all  the stuff is they're under applications like normal, so it's not a a  big problem but it's weird and I don't like it and I don't understand why the driver would effect this at all. I uninstalled the other driver from the terminal, it should be completely gone. I guess it could be something I installed here's a bit of my dpkg log, does anything in it have to do with the applications menu in unity?

2011-06-17 17:16:35 startup archives unpack
2011-06-17 17:16:38 install dkms <none> 2.1.1.2-5ubuntu1
2011-06-17 17:16:38 status half-installed dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:38 status triggers-pending man-db 2.5.9-4
2011-06-17 17:16:38 status half-installed dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:38 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:38 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:38 install nvidia-current <none> 270.41.06-0ubuntu1
2011-06-17 17:16:38 status half-installed nvidia-current 270.41.06-0ubuntu1
2011-06-17 17:16:44 status half-installed nvidia-current 270.41.06-0ubuntu1
2011-06-17 17:16:45 status unpacked nvidia-current 270.41.06-0ubuntu1
2011-06-17 17:16:45 status unpacked nvidia-current 270.41.06-0ubuntu1
2011-06-17 17:16:45 install screen-resolution-extra <none> 0.14build1
2011-06-17 17:16:45 status half-installed screen-resolution-extra 0.14build1
2011-06-17 17:16:46 status unpacked screen-resolution-extra 0.14build1
2011-06-17 17:16:46 status unpacked screen-resolution-extra 0.14build1
2011-06-17 17:16:46 install nvidia-settings <none> 270.29-0ubuntu1
2011-06-17 17:16:46 status half-installed nvidia-settings 270.29-0ubuntu1
2011-06-17 17:16:46 status half-installed nvidia-settings 270.29-0ubuntu1
2011-06-17 17:16:46 status unpacked nvidia-settings 270.29-0ubuntu1
2011-06-17 17:16:46 status unpacked nvidia-settings 270.29-0ubuntu1
2011-06-17 17:16:46 trigproc man-db 2.5.9-4 2.5.9-4
2011-06-17 17:16:46 status half-configured man-db 2.5.9-4
2011-06-17 17:16:47 status installed man-db 2.5.9-4
2011-06-17 17:16:48 startup packages configure
2011-06-17 17:16:48 configure dkms 2.1.1.2-5ubuntu1 <none>
2011-06-17 17:16:48 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status unpacked dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status half-configured dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 status installed dkms 2.1.1.2-5ubuntu1
2011-06-17 17:16:48 configure nvidia-current 270.41.06-0ubuntu1 <none>
2011-06-17 17:16:48 status unpacked nvidia-current 270.41.06-0ubuntu1
2011-06-17 17:16:48 status unpacked nvidia-current 270.41.06-0ubuntu1
2011-06-17 17:16:48 status half-configured nvidia-current 270.41.06-0ubuntu1
2011-06-17 17:17:27 status installed nvidia-current 270.41.06-0ubuntu1
2011-06-17 17:17:28 status triggers-pending python-gmenu 2.30.5-0ubuntu3
2011-06-17 17:17:28 status triggers-awaited nvidia-current 270.41.06-0ubuntu1
2011-06-17 17:17:28 status triggers-pending bamfdaemon 0.2.90-0ubuntu3
2011-06-17 17:17:28 status triggers-awaited nvidia-current 270.41.06-0ubuntu1
2011-06-17 17:17:28 status triggers-pending initramfs-tools 0.98.8ubuntu3
2011-06-17 17:17:28 configure screen-resolution-extra 0.14build1 <none>
2011-06-17 17:17:28 status unpacked screen-resolution-extra 0.14build1
2011-06-17 17:17:28 status unpacked screen-resolution-extra 0.14build1
2011-06-17 17:17:28 status half-configured screen-resolution-extra 0.14build1
2011-06-17 17:17:28 status installed screen-resolution-extra 0.14build1
2011-06-17 17:17:28 status triggers-pending python-central 0.6.15ubuntu5
2011-06-17 17:17:28 status triggers-awaited screen-resolution-extra 0.14build1
2011-06-17 17:17:28 trigproc python-central 0.6.15ubuntu5 <none>
2011-06-17 17:17:28 status half-configured python-central 0.6.15ubuntu5
2011-06-17 17:17:28 status installed screen-resolution-extra 0.14build1
2011-06-17 17:17:28 status installed python-central 0.6.15ubuntu5
2011-06-17 17:17:28 configure nvidia-settings 270.29-0ubuntu1 <none>
2011-06-17 17:17:28 status unpacked nvidia-settings 270.29-0ubuntu1
2011-06-17 17:17:28 status half-configured nvidia-settings 270.29-0ubuntu1
2011-06-17 17:17:28 status installed nvidia-settings 270.29-0ubuntu1
2011-06-17 17:17:28 trigproc python-gmenu 2.30.5-0ubuntu3 <none>
2011-06-17 17:17:28 status half-configured python-gmenu 2.30.5-0ubuntu3
2011-06-17 17:17:29 status installed python-gmenu 2.30.5-0ubuntu3
2011-06-17 17:17:29 status triggers-pending python-support 1.0.10ubuntu3
2011-06-17 17:17:29 trigproc bamfdaemon 0.2.90-0ubuntu3 <none>
2011-06-17 17:17:29 status half-configured bamfdaemon 0.2.90-0ubuntu3
2011-06-17 17:17:29 status installed nvidia-current 270.41.06-0ubuntu1
2011-06-17 17:17:29 status installed bamfdaemon 0.2.90-0ubuntu3
2011-06-17 17:17:29 trigproc initramfs-tools 0.98.8ubuntu3 <none>
2011-06-17 17:17:29 status half-configured initramfs-tools 0.98.8ubuntu3
2011-06-17 17:17:39 status installed initramfs-tools 0.98.8ubuntu3
2011-06-17 17:17:39 trigproc python-support 1.0.10ubuntu3 <none>
2011-06-17 17:17:39 status half-configured python-support 1.0.10ubuntu3
2011-06-17 17:17:41 status installed python-support 1.0.10ubuntu3
2011-06-17 17:35:32 startup archives unpack
2011-06-17 17:35:35 install nvidia-173 <none> 173.14.30-0ubuntu1
2011-06-17 17:35:35 status half-installed nvidia-173 173.14.30-0ubuntu1
2011-06-17 17:35:40 status triggers-pending man-db 2.5.9-4
2011-06-17 17:35:40 status half-installed nvidia-173 173.14.30-0ubuntu1
2011-06-17 17:35:41 status unpacked nvidia-173 173.14.30-0ubuntu1
2011-06-17 17:35:41 status unpacked nvidia-173 173.14.30-0ubuntu1
2011-06-17 17:35:41 trigproc man-db 2.5.9-4 2.5.9-4
2011-06-17 17:35:41 status half-configured man-db 2.5.9-4
2011-06-17 17:35:43 status installed man-db 2.5.9-4
2011-06-17 17:35:43 startup packages configure
2011-06-17 17:35:43 configure nvidia-173 173.14.30-0ubuntu1 <none>
2011-06-17 17:35:43 status unpacked nvidia-173 173.14.30-0ubuntu1
2011-06-17 17:35:43 status half-configured nvidia-173 173.14.30-0ubuntu1
2011-06-17 17:36:22 status installed nvidia-173 173.14.30-0ubuntu1
2011-06-17 17:36:23 status triggers-pending python-gmenu 2.30.5-0ubuntu3
2011-06-17 17:36:23 status triggers-awaited nvidia-173 173.14.30-0ubuntu1
2011-06-17 17:36:23 status triggers-pending bamfdaemon 0.2.90-0ubuntu3
2011-06-17 17:36:23 status triggers-awaited nvidia-173 173.14.30-0ubuntu1
2011-06-17 17:36:23 trigproc python-gmenu 2.30.5-0ubuntu3 <none>
2011-06-17 17:36:23 status half-configured python-gmenu 2.30.5-0ubuntu3
2011-06-17 17:36:23 status installed python-gmenu 2.30.5-0ubuntu3
2011-06-17 17:36:23 status triggers-pending python-support 1.0.10ubuntu3
2011-06-17 17:36:23 trigproc bamfdaemon 0.2.90-0ubuntu3 <none>
2011-06-17 17:36:23 status half-configured bamfdaemon 0.2.90-0ubuntu3
2011-06-17 17:36:23 status installed nvidia-173 173.14.30-0ubuntu1
2011-06-17 17:36:23 status installed bamfdaemon 0.2.90-0ubuntu3
2011-06-17 17:36:23 trigproc python-support 1.0.10ubuntu3 <none>
2011-06-17 17:36:23 status half-configured python-support 1.0.10ubuntu3
2011-06-17 17:36:26 status installed python-support 1.0.10ubuntu3
2011-06-17 17:42:30 startup archives unpack
2011-06-17 17:42:32 install nvidia-common <none> 0.2.30
2011-06-17 17:42:32 status half-installed nvidia-common 0.2.30
2011-06-17 17:42:32 status unpacked nvidia-common 0.2.30
2011-06-17 17:42:32 status unpacked nvidia-common 0.2.30
2011-06-17 17:42:33 startup packages configure
2011-06-17 17:42:33 configure nvidia-common 0.2.30 <none>
2011-06-17 17:42:33 status unpacked nvidia-common 0.2.30
2011-06-17 17:42:33 status unpacked nvidia-common 0.2.30
2011-06-17 17:42:33 status unpacked nvidia-common 0.2.30
2011-06-17 17:42:33 status half-configured nvidia-common 0.2.30
2011-06-17 17:42:36 status installed nvidia-common 0.2.30

---

### Post by wildmanne39 on 2011-06-18
Hi, if you look in that list it shows a lot of half installed packages for nvidia and one for desktop lighting or something like that, you need to install them all the way or get rid of them completely, probably best to get rid of them completely, it is possible that will not fix your problem but it sure is not good. I think it will if you get all those gone. you can try this command.
```
sudo rm  /var/lib/apt/lists/partial/*
```
```
sudo apt-get update
```

---

### Post by someitalian123 on 2011-06-18
I looked in the partial folder with nautilus. There is nothing in their for me to delete, I had  "Show Hidden Files" selected, there's absolutely nothing in the folder, so I didn't try the commands you suggested. And also I wasn't trying to get rid of the driver from the repositories, I was trying to get rid of the driver that comes in a .run, I didn't get it from apt-get or aptitude. I used sudo sh NVIDIA.run -uninstall to get rid of it.

---

### Post by wildmanne39 on 2011-06-18
> **someitalian123 said:**
> I looked in the partial folder with nautilus. There is nothing in their for me to delete, I had  "Show Hidden Files" selected, there's absolutely nothing in the folder, so I didn't try the commands you suggested. And also I wasn't trying to get rid of the driver from the repositories, I was trying to get rid of the driver that comes in a .run, I didn't get it from apt-get or aptitude. I used sudo sh NVIDIA.run -uninstall to get rid of it.Hi, ok did you look at the information you post though? did you see the half installed packages and half configured one?

---

### Post by someitalian123 on 2011-06-18
If there is nothing in that folder what good would sudo rm  /var/lib/apt/lists/partial/* actually do. Tell me how to fully install the packages instead of deleting them. Which ones are done only half way? I see stuff that says half installed then further down the list it says it's installed. I haven't looked at the whole thing, but maybe your not looking at the whole thing either.

---

### Post by wildmanne39 on 2011-06-18
> **someitalian123 said:**
> If there is nothing in that folder what good would sudo rm  /var/lib/apt/lists/partial/* actually do. Tell me how to fully install the packages instead of deleting them. Which ones are done only half way? I see stuff that says half installed then further down the list it says it's installed. I haven't looked at the whole thing, but maybe your not looking at the whole thing either.Hi, you could be right, hopefully someone else will jump in here and solve your issue. If it is still only with the applications in dash that will hopefully be fixed with a update. To be honest sometimes it acts a little strange but I do not use mine so I do not notice it, I have a awn launcher with the menu on it like in gnome2.

---

