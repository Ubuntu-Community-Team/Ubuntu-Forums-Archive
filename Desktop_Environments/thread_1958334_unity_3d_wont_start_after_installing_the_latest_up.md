---
title: "unity 3d wont start after installing the latest updates from yesterday"
date: 2012-04-14
forum: Desktop Environments
---

### Post by sshatery on 2012-04-14
Hello guys,
yesterday the update manager notified me to install few updates such as Google chrome and some updates for nVidia graphic card. as usual i just clicked on install updates and after updates i just restart my system. but i was not able to start the unity 3d and Gnome. but i still can start unity 2d. so i tried to restart the unity but still didnt work. i went to the additional drivers and removed the "NVIDIA accelerated graphics driver (version current)[recommended]" and after restarting the system i was able to get into the unity 3d and gnome but without any 3d effect and also my system is kinda laggy. i think there must be something wrong with the new update or i dont know. oh, i just have to inform you that this is my office system and its an e-machine EL1352 with GeForce 6150SE graphic.

Thanks guys. i know you can help me like always.

---

### Post by Pablo Pablovski on 2012-04-14
I;m having a similar problem with both ubuntu 11.04 and kubuntu 11.10 on the same machine. I think it's something to do with the Nvidia driver - I have an 8800 GTS, 640MB. 

The desktop loads, slowly, at start up but I can't do anything - clicking on a launcher or an icon, or right-clicking to get a context menu - nothing works.

I also have Win7 on the same system, and it's ok with the recent upgrade of the Nvidia driver (v290). 

I've tried updating the 11.04 install with newer Linux drivers (v295.60 I think) to no improvement. I suspect an Xorg problem but I'm not sure what else to try.

---

### Post by 3Miro on 2012-04-14
Try reinstalling the driver: remove, reboot, activate again, reboot.

---

### Post by fioan89 on 2012-04-14
Same here!Yesterday i installed the latest updates.Today when i turned  on my ubuntu,unity is running in 2d mode.

Tried to log on unity 3d but no  success.
So i run /usr/lib/nux/unity_support_test -p and it tell's me that i  don't have support for GL vertex buffer object.The funny thing is  glxinfo doesn't report any problem.Next thing: i got on amd website and  downloaded latest catalyst.After that i run apt-get purge fglrx, reboot  and install the new catalyst driver.

Now everything is good but at some point i noticed that my notebook is  running quite slow.Running top showed me the problem:compiz is eating a  lot of my cpu.For example if i start moving some windows then compiz is  eating 60-70% of my cpu.I thought that a reinstall of ubuntu would do  better but then i remembered that 12.04 will be out soon ,so i said  let's install gnome-shell and give it a ride.Now  surprize,surprize:gnome-shell is running slow.I fired up top and  gnome-shell process is eating the same amount of cpu like compiz in  unity.

Finally i came here to you guys,maybe you can give me some advices on what  to do next (i'm not in the mood to reinstall ubuntu again) .

My specs are:
Notebook Acer Aspire with a Pentium T4300 dual core CPU and ATI Mobility Radeon HD 4570 with latest Ubuntu 11.10

Thank you for you help!

---

### Post by Pablo Pablovski on 2012-04-14
Purging / reinstalling the 290-series driver didn't help. Neither did reconfiguring xorg. 

I think I'll try purging the latest 290 driver, and install /activate the current 173-series driver to compare. I guess if that doesn't make a difference, it's not an nVidia driver issue. The kernel was updated at the same time on my 11.10 and near the same time on 11.04 (different kernel versions). 

Could the same faulty patch have been applied to both 2.6 and 3.0 series kernels?

---

### Post by bogan on 2012-04-14
Hi! **all**,

I had exactly similar problems following the recent update of nvidia-current with 10.04 and even worse with 11.10, a BusyBox hang-up that would not even boot to recovery.

I cured both by using ```
 sudo nvidia-installer -f
```Which downloaded and installed the 295.33 driver, after uninstalling the old 290.10 and the nvidia-current faulty drivers.

 You have to do it from a Text terminal, or after running```
 sudo service gdm stop  # 'lightdm'  if =>11.04 instead of 'gdm' 
```from a GUI terminal, as Xserver must not be running.  To restart:```
sudo service gdm start  # 'lightdm' if =>11.04 instead of 'gdm' 
``` Or reboot. 

If you need more info see MAFoElffen's Sticky in the Installation & Upgrade Forum, Post #280.
[http://ubuntuforums.org/showthread.php?t=1743535&page=71](http://ubuntuforums.org/showthread.php?t=1743535&page=71)

Chao!,** bogan.**

---

### Post by rtimai on 2012-04-14
Unity 3D doesn't start on my ATI graphics system either. What I am seeing is the Nautilus menu in the top bar, the desktop background, and nothing else. I can navigate the local file system fine, and start apps from the /user/bin menu (maybe not recommended.) 

Anyway, I don't think it's graphics-related. I'm alternately running LXDE (glad I installed it,) and it works fine, so I don't think it's X-related either as LXDE is also X-based. 

It may be LightDM, but I'm an hesitant to try the LightDM restart until I know more about what happened. 

I think it is related to the following much-repeated error message in the .xsession-errors log:

(nautilus:2377): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

UPDATE SAT 14/04/2012
FIXED: After the Canonical updates served today I was able to successfully log in to the Unity desktop again. Didn't pay attention to what was updated, however. I checked Synaptic Package Manager History, but didn't find updates logged. Anyway, I'm glad I didn't try too many fixes.

---

### Post by lolpenguin on 2012-04-14
Hmm? The xorg and driver updates worked for me...

---

### Post by Pablo Pablovski on 2012-04-15
Ok, tried downgrading to the 173 driver in 11.04 - that made the problem worse, if anything - the desktop was frozen altogether.

So, I purged it and reinstalled / activated the 295 driver - and the system now seems ok again. No desktop freezing issues, launchers work. Weird. I'll try the same "fix" in 11.10.

---

### Post by Pablo Pablovski on 2012-04-17
Arrgh... My 11.04 install, which worked ok after upgrading the Nvidia driver, reverted to borked after a reboot. Same with the 11.10 install of kubuntu, kernel 3.0.0-19.

I've tried bogan's suggesiton of upgrading the Nvidia driver to the version from the Nvidiai website, usn ghe .run file - 295.40. Still no joy, in fact it broke the 11.10 install completely.

So, both are restored from back up until the issue is fixed - can't help feeling there's something more to this.

---

### Post by bogan on 2012-04-17
Hi! all,

It seems likely from other similar threads that the problems from the nvidia-current update arise from the installation using the wrong kernal-headers to construct the kernal module.

The cure - if: 
 ```
sudo nvidia-installer -f
```does not work - is to purge the remnants of previous installations and update the headers, then run the downloaded nvdia .run file with 'sh'.

As per my previous Post: If you need more info see MAFoElffen's Sticky in the Installation & Upgrade Forum, Post #280. 
There is also a full index on Post #2 with a step-by-step troubleshooter in Post #1.
[http://ubuntuforums.org/showthread.p...743535&page=71]("http://ubuntuforums.org/showthread.php?t=1743535&page=71")

As for the similar problems with ATI/AMD cards, I can only assume something similar happens with them - but that is sheer guesswork.

Chao!, bogan.

---

### Post by bogan on 2012-05-04
Hi!,** All,** 

Deleted, out-of date.

Chao!, **bogan**

---

### Post by bogan on 2012-05-17
Hi!,** All**.

[COLOR=Blue]There is a new nvidia driver version 295.53 available [/COLOR]from nvidia downloads.  This Link is for the 32 bit version, check you get the correct one.
[http://www.nvidia.co.uk/object/linux...driver-uk.html]("http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html")

[COLOR=RoyalBlue]**Edit: Updated Thursday May 17th; **[/COLOR]     

      	Code:
 	nvidia-installer --latest 
 now returns: v295.53 and the currently installed version, without altering anything.
     

      	Code:
 	nvidia-installer -f 
 will install 295.53 after un-installing the previous version.

NVNews says of version 295.53:
QUOTE:
**Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**,
 [GeForce4]("http://viglink.pgpartner.com/rd.php?r=10313&m=878281881&q=o&priceret=87.73&pg=%7E%7E3&k=2b6229593608c3c1fb499d0ca9880634&source=feed&url=http%3A%2F%2Fmicropartsusa%2Ecom%2F31p6953%2Dibm%2Dnvidia%2Dgeforce4%2Dmx440%2D64mb%2Dagp8x%2Datx%2Dgraphics%2Dcard%2Dw%2Do%2Dcable%2Dnew%2Dbulk%2Din%2Dstock%2Ehtml&st=feed&mt=%7E%7E%7E%7E%7E%7E%7E%7En%7E%7E%7E") and older GPUs are supported through the **96.43.xx** and **71.86.xx** [NVIDIA]("http://www.nvidia.com/") legacy graphics drivers.
 GeForce FX GPUs are supported through the **173.14.xx** NVIDIA legacy graphics drivers.

[B]
bogan.[/B]

---

