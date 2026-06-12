---
title: "continue to use ubuntu 16 and update gcc to 9 ?"
date: 2021-06-18
forum: Desktop Environments
---

### Post by zhuxysoler on 2021-06-18
Hi,
I use ubuntu 20 for several days. I find it is a little heavy for my laptop (Intel® Core&#8482; i5-6300HQ CPU @ 2.30GHz × 4 NV117 / Mesa Intel® HD Graphics 530 (SKL GT2), 20GB RAM). I often run vmware and total RAM mostly keeps at 10 GB. Sometimes a little stuck, not response quickly. I also try cinnamon and Mate desktop. The quick response of these two desktop also have a problem. A LibreImpress file with a ~45MB size will have display problem after opening for a while. All the pictures inside can not been seen, see [https://imgur.com/XVU05hO](https://imgur.com/XVU05hO)  [https://imgur.com/Pv393gO](https://imgur.com/Pv393gO). So I return to ubuntu gnome. But this problem also happened, just take a little more time to appear this problem. 
I have no idea now. I also try ubuntu unity in VMware. Set 2 core and 3GB for it. I find the response is not quick enough. 
So I have a idea to use ubuntu 16 again for its quick response, and install gcc 9 and python 3.8 for it. Does this proposal work? What is the shortcoming? Is it stable? Actually I want a good distro for daily working.

---

### Post by ajgreeny on 2021-06-18
No, that will not work, and as 16.06 has no further upgrades or package installation available, having lost support 2 months ago, you will now find it is impossible to use safely any more.

I suspect that trying to open a 45M sized Libreoffice Impress file is always going to be slow on a machine using the gnome DE, but with only an Intel HD6300 graphics system, which I think is what you mean by ***intel 6300hq***.  The Ubuntu gnome DE of Ubuntu 20.04 requires good 3D graphics to work as effectively as possible and I think with your hardware you will do better with a different *ubuntu version such as Xubuntu or Lubuntu 20.04.

---

### Post by guiverc on 2021-06-18
If you're talking about Ubuntu Core 16, it is supported until 2026 or has a ten year life span.

Applications in *year* format products are the same on all releases, so when should you upgrade a Ubuntu Core 16 system to Ubuntu Core 18, no applications need be changed, as *snaps* are the same for all releases; the upgrade includes only the base operating system being upgraded without any change of apps.  The same applies if you move to Ubuntu Core 20.

That does not apply with *year.month* products, as there the applications are *deb* packages built for a specific release, with specific dependencies that were found in that said release. However you mention only *year* systems, which are *snap* only with Ubuntu having *snap* only products since 2016 or Ubuntu Core 16.

Also note, whilst GNOME was packaged to run on *year* products, they were designed for use in headless environments, so you shouldn't expect the same performance or experience found on a desktop intended release (which are all *year.month* products).

If you mean Ubuntu 16.04 then please say so, as it's a different product.

Ubuntu 16.04 LTS has reached the end of it's standard support, ESM support is available though. See

- [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)
- [https://ubuntu.com/blog/ubuntu-16-04-lts-transitions-to-extended-security-maintenance-esm](https://ubuntu.com/blog/ubuntu-16-04-lts-transitions-to-extended-security-maintenance-esm)

---

### Post by zhuxysoler on 2021-06-18
Thanks your suggestion. The hardware configurations are Intel® Core&#8482;  i5-6300HQ CPU @ 2.30GHz × 4 NV117 / Mesa Intel® HD Graphics 530 (SKL  GT2), 20GB RAM. 
*ubuntu, such as xubuntu, lubuntu, I have some using  experience. I used to use xfce in ubuntu 16 and  in subsystem ubuntu  18 under win10.  XFCE can not run stably in the both cases. Because I  will run some computation terminals, edit LibreImpress odp file at the  same time, the XFCE desktop will suddenly restart, all runing process  ended. So I don't know if others have similar experience of XFCE? Does  an original XFCE desktop in Xubuntu perform better than a extra  installed XFCE in ubuntu? So I am testing Lubuntu in VM ware first.

---

### Post by grahammechanical on 2021-06-18
You have powerful hardware with a massive amount of memory. So, if you are experiencing a slow down in the video display I doubt very much if the Desktop Environment (DE) is causing the problem. Using a DE that requires less memory than another DE should help a little bit. But you say that it does not help. The problem lies else where.

> Due to its lack of dedicated graphics memory or eDRAM cache, the HD 530  has to access the main memory (2x 64bit DDR3L-1600 / DDR4-2133).

[https://www.notebookcheck.net/Intel-HD-Graphics-530.148358.0.html](https://www.notebookcheck.net/Intel-HD-Graphics-530.148358.0.html)

You are doing memory intensive work. The OS will set aside some memory as cache memory in case more memory is needed by the applications. The video adapter is using some of your RAM. So, although it seems that you still have half your RAM available that is not actually the case.

When the computation program needs more RAM where does it get it from? Editing large Impress files will make great demands on video memory. which is actually RAM. Where does Impress get more RAM from? And when there is no more RAM available what do you think will happen?

Regards

---

### Post by zhuxysoler on 2021-06-18
> **grahammechanical said:**
> You have powerful hardware with a massive amount of memory. So, if you are experiencing a slow down in the video display I doubt very much if the Desktop Environment (DE) is causing the problem. Using a DE that requires less memory than another DE should help a little bit. But you say that it does not help. The problem lies else where.



[https://www.notebookcheck.net/Intel-HD-Graphics-530.148358.0.html](https://www.notebookcheck.net/Intel-HD-Graphics-530.148358.0.html)

You are doing memory intensive work. The OS will set aside some memory as cache memory in case more memory is needed by the applications. The video adapter is using some of your RAM. So, although it seems that you still have half your RAM available that is not actually the case.

When the computation program needs more RAM where does it get it from? Editing large Impress files will make great demands on video memory. which is actually RAM. Where does Impress get more RAM from? And when there is no more RAM available what do you think will happen?

Regards

Thanks your suggestions. Yes.Some package installed maybe not compatible. But I am not sure where is the problem is. During the using, sometimes the OS will remind of the errors whether to send. Because linux is not good at MS document editing, so I need to run VMware. I also use LibreCal to process data with a more than 50MB of size. Copy and paste all the columns of data are often done between libreCal and QtiPlot. The operation seems not smooth as in ubuntu 16.04lts. 
Using Ubuntu as a daily work OS, I still prefer to reduce the installation of packages to avoid potential risk. But I have to try some new packages. Linux 16.04 which is the first distro I engaged takes me a long time to familiar and try and error. 
In total, I want a distro which is lightweight but guarantee the basic figure display in document, large size allowed for coping and pasting,

I am testing Lubuntu desktop in the ubuntu 20.04 to check the display problem will reproduce again. When coping all columns in a LibreCal file, RAM usage increase from 7GB to 14GB,and LibreCal get stuck. No significant SWAP usage increase. I give a 15GB for the SWAP space. The display problem doesn't happen in lubuntu. A good signal.

---

### Post by monkeybrain20122 on 2021-06-19
You have a powerful machine with lots of ram, I doubt that your problem has anything to do with heavy load, you don't need a super computer to run Ubuntu even with the gnome-de. I can't say for sure but it seems that a lot of issues about slow and unresponsive desktop can be traced to graphic driver problems. Maybe try upgrading your driver. Since you have an intel card [https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa](https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa)

---

### Post by zhuxysoler on 2021-06-19
> **monkeybrain20122 said:**
> You have a powerful machine with lots of ram, I doubt that your problem has anything to do with heavy load, you don't need a super computer to run Ubuntu even with the gnome-de. I can't say for sure but it seems that a lot of issues about slow and unresponsive desktop can be traced to graphic driver problems. Maybe try upgrading your driver. Since you have an intel card [https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa](https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa)

Thanks. I am testing the Lubuntu desktop. Ram keeps at 5-6GB. The LibreImpress file display normally. The system was stuck sometimes during coping data from LibreCal sheet file to Qtiplot. Are there some method to improve the copy/paste operation by increasing its capability of data transmission.?

---

### Post by monkeybrain20122 on 2021-06-20
> **zhuxysoler said:**
> Thanks. I am testing the Lubuntu desktop. Ram keeps at 5-6GB. The LibreImpress file display normally. The system was stuck sometimes during coping data from LibreCal sheet file to Qtiplot. Are there some method to improve the copy/paste operation by increasing its capability of data transmission.?

I don't know how you do your copy/paste but my experience is using the command line (cp, mv etc) is a lot faster than the GUI.

As I said your sluggish desktop experience (not related to copy/paste) is likely due to graphic driver issue. Lubuntu feels faster not because it is 'light' (with your specs it shouldn't make a difference whatever DE you use in terms of resource demand, the difference is negligible) but maybe due to lack of composting (do they still use LXDE?) hence the driver bugs (if present) are not exposed.

As for your original question, yes, you can install whatever gcc from source provided it is not too old or too new so it can be compiled using the system's gcc. I have had gcc9 on Ubuntu 16.04 before its EOL, you can then use update-alternatives to choose your gcc version  (but programs compiled with your local gcc may not run  if it has a run time dependency on libstdc++6 since it will find the system's version which doesn't match your gcc's, workaround is to set LD_LIBRARY_PATH to point to the folder that contains libstdc++6 in your local gcc folder when you run application,--or start it with a script that sest LD_LIBRARY_PATH)

---

