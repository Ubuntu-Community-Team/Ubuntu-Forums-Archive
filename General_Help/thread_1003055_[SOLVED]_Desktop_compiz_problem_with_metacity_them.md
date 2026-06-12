---
title: "[SOLVED] Desktop compiz problem with metacity theme"
date: 2008-12-05
forum: General Help
---

### Post by EreboShade on 2008-12-05
i have this problem! with metacity theme i see this

[[IMG]http://img229.imageshack.us/img229/8813/problemadesktopcs9.th.png[/img]](http://img229.imageshack.us/my.php?image=problemadesktopcs9.png)

with clearlooks theme, this problem is solved.

i have updated ubuntu 8.04 in ubuntu 8.10


can i solve it?

---

### Post by EreboShade on 2008-12-07
up

---

### Post by Forlong on 2008-12-07
What Metacity theme is it?

---

### Post by EreboShade on 2008-12-07
it's human metacity theme. i've changed only the color. it's the same!

the problem there is with the original human themes, too!

---

### Post by EreboShade on 2008-12-09
i solved all.

see [http://ubuntuforums.org/showthread.php?t=1004901](http://ubuntuforums.org/showthread.php?t=1004901)

this steps

This is how I installed the Nvidia 180.06 driver manually

1: goto Synaptic Package Manager and search for linux-source-2.6.27 and click for installation.

2. go here : [http://www.nvidia.com/object/linux_d...32_180.06.html](http://www.nvidia.com/object/linux_d...32_180.06.html) and download the NVIDIA-Linux-x86-180.06 pkg1.run file and move it to your home folder

for 64bit [http://www.nvidia.com/object/linux_display_amd64_180.06.html](http://www.nvidia.com/object/linux_display_amd64_180.06.html)

these next steps you will have to write down cause you will be going to a tty session and wont have a graphical desktop anymore

3: press Ctrl-Alt-F1
it will leave the desktop and go into the tty session and will ask for your sign-in name and password type those in

4: next type sudo /etc/init.d/gdm stop......it will ask for your password type in in this stops your x-server to install the driver

5: next type ls......this lists what is in your home folder the nvidia driver should be listed along with your folders

6: next type sudo sh NVIDIA-Linux-x86-180.06-pkg1.run......make sure it is typed exactally like that then follow the steps that come up on the screen answer yes to all questions it should build the new nvidia driver

7: after the driver is built you want to type
sudo /etc/init.d/gdm start......this will restart your x-server and bring your graphical interface back

it should move your nvidia x-server settings to application/system tools...check that to make sure the 180.06 driver is listed there and all window problems should be gone

hope this helps and you can understand the steps

---

### Post by eternalnewbee on 2008-12-09
Glad your problem is solved. Don't forget to mark it so, under Thread Tools, at the top of this page.

---

### Post by EreboShade on 2008-12-09
> **eternalnewbee said:**
> Glad your problem is solved. Don't forget to mark it so, under Thread Tools, at the top of this page.

yes,i do already!

---

