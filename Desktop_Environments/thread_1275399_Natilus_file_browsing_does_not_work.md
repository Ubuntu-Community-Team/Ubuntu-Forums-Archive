---
title: "Natilus file browsing does not work"
date: 2009-09-25
forum: Desktop Environments
---

### Post by jm2 on 2009-09-25
I have an Ubuntu - intrepid on new laptop HP 60-445DX notebook.

Kernel 2.6.27-14

I had to install the EnvyNG- NVIDIA graphic selection program to get the screens displays to work properly. It has installed 177.82 drivers.

Now when when I use OpenOffice, Evolution, Blackboard (school program) from Firefox to select a file. The browser just hangs and won't select anything. I can cancel out. I can select from Places, just fine and go anywhere from there.

II managed to un-install openoffice-org (I think that was the one for the browser here) and now it uses dolphin.  I have no clue why it is having issues on all these different programs. I found nothing else on this matter.

The only thing I can think is there is some configuration file in Evolution and Firefox that needs to be re-set. However, I have no clue what else to try.


Any Suggestions?

If you need any other information, let me know.

---

### Post by chenxiaolong on 2009-09-25
I have had that issue before. It's not a problem with the applications, but rather the Nvidia driver. When you click areas in the problem, the thing won't show up, but it's actually there. To solve this problem, uninstall the Nvidia driver using EnvyNG and install the Ubuntu Nvidia driver using the Restricted Hardware Drivers dialog box or install the nvidia-glx package.

I hope this works for you

--------------------------

I'm turning 14 tomorrow (9/26/1995)

---

### Post by jm2 on 2009-09-25
I unstalled EnvnNG, and I am still having the same issues.

I went into System, Drivers, and selected 180 as recommended. This made problems worse. My screens freeze, ie: presentation. In Evolution, I tried to add an attachment, and I get a sort-of outline where the browser is supposed to be, and it just hangs, must power off system, can't get a logon on F2.

I went into System, Drivers, and put in 177. And I am now back to where I started with.
This is what is installed for Nvidia in Synaptic:
nvidia-settings
nvidia-177-kernel-sources
nvidia-common
nvidia-71-modaliases
nvidia-173-modaliases
nvidia-177-modaliases
nvidia-180-modaliases
nvidia-90-modaliases
nvidia-glx-177
gimp-normal-map
smart-dimmer
jockey-gtk
jockey-common

should I not have one of these installed?

Anyone else have other suggestions?

Yes, I did re-boot after each change.
[I]
Thanks
[/I]
I don't know if re-installing my evolution would make sense, since I am having this issue with multiple packages.

---

### Post by chenxiaolong on 2009-09-26
Sorry, my instructions were unclear. You shouldn't have uninstalled EnvyNG. You should have opened it and chose the option to uninstall the Nvidia driver. You can reinstall the EnvyNG package to do so. Then you should run ```
sudo apt-get update
``` in the terminal to update the list of packages (because the search for Nvidia should have more results). Then run ```
sudo apt-get install nvidia-glx-new
``` to install the nvidia-glx-new package. I suggest you install the package using the terminal because the package might not show up in Synaptic. 

I hope this works for you.

By the way, you should upgrade to Ubuntu Jaunty 9.04, as it has newer drivers.

---

### Post by jm2 on 2009-09-30
I re-installed the ENVNG program. I de-selected the driver. When I reboot, it now comes up in low graphics mode. 

This solves my nautilus problem at the moment.

I went to do the apt-get nvida-new-glx, and it said this was replaced by several nvidia-xxx drivers which are already currently installed from above list.

My screen refresh/display rate is very slow and awkard. 

Any suggestions on how to fix my low graphics mode, and keep the nautilus program from hanging at the same time?

Thanks.

p.s. chenxiaolong - happy birthday!

---

### Post by chenxiaolong on 2009-09-30
Thanks!!

Several nvidia-* packages? Could you list all of them? You might need to uninstall some and install them again. I'll help you out if you can give me the nvidia packages installed.

---

### Post by jm2 on 2009-10-09
I gave up on this version on 8.10. I believe this is a real bug in 8.10. 

I installed the Beta version of 9.10 Karmic and my screen display works now much better.

thanks for your help.

---

### Post by chenxiaolong on 2009-10-09
I'm glad it works. I had to upgrade to the Karmic beta too to fix my wireless problems. Karmic seems to have solved most problems.

---

