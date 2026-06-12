---
title: "[SOLVED] Ragnum Online"
date: 2008-08-14
forum: Gaming &amp; Leisure
---

### Post by naknak987 on 2008-08-14
Could someone tell me what might cause a problem like this. [IMG]http://www.freewebs.com/naknak987/Screenshot.png[/IMG] My Hardware meets the requirements for this game. I don't exactly know what my hardware is. Is there a command or something that will tell me what hardware I have? My thinking is that when I had windows I played Oblivion without any problems, I know windows and Linux are different and the the two games are different but if my comp could handle oblivion should it not handle Ragnum? Just a thought.

---

### Post by cristo-father on 2008-08-14
disable compiz.

---

### Post by naknak987 on 2008-08-14
If doing this ```
metacity --replace
``` will disable compiz then it didn't work.



When I enabled compiz I got this error? 
```
naknak987@naknak:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:05.0 0300: 10de:0240 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


```

---

### Post by cristo-father on 2008-08-14
I disable compiz by going to system > Preferences > Appearance > Visual Effects.
Then click on none.

---

### Post by naknak987 on 2008-08-14
Nether way worked. Maybe I installed wrong? All I did to install was download the RagnumOnline_32 file from there site and then did this in the terminal ```
chmod +x RagnumOnline_32
``` then I just double clicked the file and boom, installer ran.

---

### Post by cristo-father on 2008-08-14
[http://ubuntuforums.org/showthread.php?t=615246&highlight=regnum+online](http://ubuntuforums.org/showthread.php?t=615246&highlight=regnum+online)

---

### Post by naknak987 on 2008-08-14
Ok, I did what I chould with that but it really didn't help much. I need to go to bed, maybe it will work after a good nights sleep. Thanks for the help anyway. night night. I'll post resaults tomarrow.

---

### Post by iheartubuntu on 2008-08-14
I had this same prob with my nvidia card. So *IF* you have an nVidia graphics card...  go to applications>add/remove> then install sysinfo. Then go into the sysinfo program and you should be able to tell if you have nvidia card. If its an ATI card it should already work OK.

If you do have nvidia, you should go here: and download the correct drivers..

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

If you have Ubuntu 8.04, then open a terminal and type this:

> sudo apt-get install envyng-gtk

If you have Ubuntu 7.10 or older, then download this file and double click it to install:

[http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb)

If SysInfo told you that you had an ATI card, install the ATI drivers within Envy (you can find envy in "applications>system tools"). This should update your ATI drivers to the best ones. But if you have nVidia card, then install the nVidia drivers. Pick the correct one or it will screw up your video drivers big time!

Install which ever drivers you pick. Make sure they are the correct ones! -dont install ATI if you have nVidia!. Reboot and then see if the game works better.

If you still have that prob (after installing nvidia drivers), You need to go into your synaptic package manager (system>admin>synaptic) and do a search on "nvidia-glx-new" and select for installation the nvidia drivers that start with "173". These are the latest drivers which will fix those graphics problems.

That should work. It did for me.
[B][COLOR="Red"]
I recommend not installing any drivers if you cant figure out what card you have :)[/COLOR][/B]

---

### Post by ceno-byte on 2008-10-23
i know this is a old thread but i followed the steps above that shirteesdotnet provided and it does in fact solve the problem

---

### Post by naknak987 on 2008-10-24
Your right, it does solve the problem.

---

### Post by vanquishedangel on 2008-12-05
yes this thread is old but for anyone playing this game it still can be difficult so I will post what solved it for me, I got an error that my graphics card was not supported when trying to run this game but on the website it said it was supported. I have an ati mobility radeon 7500. its old but still works, what you need to do for this is go into the terminal and type "sudo apt-get install driconf" once installed and the terminal has finished type "driconf" and the program should open, if not you can go to system-preferences-dri 3d acceleration. Now for me there is alot of room here, to get it working you need to enable s3tc texture compression. to do this go to the second tab or image quality tab, and it should be the fourth one down. The box should say yes if not click on it, also for those that have my exact or this might work for others as well switch the texture color depth to "prefer 32 bits per texel" under the same tab. This worked to help better render the graphics after it was working.

---

