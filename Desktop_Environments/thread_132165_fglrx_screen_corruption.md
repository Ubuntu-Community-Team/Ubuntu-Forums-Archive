---
title: "fglrx screen corruption"
date: 2006-02-17
forum: Desktop Environments
---

### Post by SuperBOB on 2006-02-17
Hi,

I have just switched to Ubuntu on my laptop but I am encountering some problems getting DRI working without massive screen corruption :-? 
I have harassed everyone in #ubuntu on Freenode and still can't get it to work..


[http://ps-aux.org/lspci]("http://ps-aux.org/lspci")
[http://ps-aux.org/dmesg.log]("http://ps-aux.org/dmesg.log")
[http://ps-aux.org/Xorg.0.log]("http://ps-aux.org/Xorg.0.log")
[http://ps-aux.org/lsmod.log]("http://ps-aux.org/lsmod.log")
[http://ps-aux.org/xorg.conf]("http://ps-aux.org/xorg.conf")

If I remove xorg.conf and let X sort itself out, then my screen is perfect, except DRI is disabled.  

Thanks for reading :)

---

### Post by SuperBOB on 2006-02-18
Could an admin move this to the correction section for me please? Sorry

---

### Post by SuperBOB on 2006-02-18
Im still having this issue if somebody who has a working DRI enabled FireGL 9000 (ATI Radeon 9200) could post and give me some advice, I would be grateful

---

### Post by Ocxic on 2006-02-18
I have DRI working on my ATI 9200 SE this is how i got mine working

to make sure this works, remove all of the drivers and modules from befor using this thread:
[http://www.ubuntuforums.org/showthread.php?t=75378&highlight=ATI](http://www.ubuntuforums.org/showthread.php?t=75378&highlight=ATI)

I got these instructions form here: [http://www.ubuntuforums.org/showthread.php?t=125974&highlight=ATI](http://www.ubuntuforums.org/showthread.php?t=125974&highlight=ATI)

```

wget -c --no-check-certificate https://www2.ati.com/drivers/linux/ati-driver-installer-8.21.7-i386.run

sudo apt-get install fakeroot gcc-3.4 module-assistant build-essential debhelper

fakeroot ./ati-driver-installer-8.21.7-i386.run --buildpkg Ubuntu/breezy 

sudo dpkg -i fglrx-control_8.21.7-1_i386.deb fglrx-kernel-source_8.21.7-1_i386.deb fglrx-sources_8.21.7-1_i386.deb xorg-driver-fglrx_8.21.7-1_i386.deb xorg-driver-fglrx-dev_8.21.7-1_i386.deb

sudo module-assistant build,install fglrx-kernel

echo fglrx | sudo tee -a /etc/modules
sudo sed -e 's/"ati"/"fglrx"/' -i /etc/X11/xorg.conf

```

reboot your caomputer after your done, and you should be good, to check if DRI is enabled type this in a terminal:
cat /var/log/Xorg.0.log | grep dri
you should see somewhere where it loads the dri modules, if there are no errors your good to go.

---

### Post by SuperBOB on 2006-02-18
I have already done that,

The problem isn't that DRI wont work, the problem is with screen corruption when using FGLRX

In my original post I included my logs, which show DRI is enabled correctly

---

### Post by Ocxic on 2006-02-18
have you tried sudo dpkg-reconfigure xserever-xorg and tryed different monitor sizes?? what exactly do you mean by screen corruption?

---

### Post by SuperBOB on 2006-02-19
I have solved this problem by downgrading my ATI drivers

There appears to be a problem with 9200 Mobility and the latest drivers

For future reference the laptop im using it an HP - Compaq NX 7010
Thanks for your help

---

