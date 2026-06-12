---
title: "Problem with Ati Driver"
date: 2009-06-11
forum: General Help
---

### Post by ubfu on 2009-06-11
I just installed ubuntu 8.04 but the fan speed of my graphic card is running 100%

So I just install the normal opensource driver from System>administration>hardware and select the Ati driver.
After I install reboot , still it doesn't solve the fan speed.

I went to Ati driver and download ati-driver-installer-9-5-x86.x86_64.run including the manual.

Uninstall the opensource ati driver and install ati-driver-installer-9-5-x86.x86_64.run .Reboot and I got blank screen.
Went to the forum and search on how to uninstall 

[http://ubuntuforums.org/showthread.php?t=1179913&highlight=ati+radeon+9600XT](http://ubuntuforums.org/showthread.php?t=1179913&highlight=ati+radeon+9600XT)
> **Legace said:**
> ATi Catalyst Control Center doesn't support your card on Ubuntu 9.04.
You need to uninstall the driver:

Reboot PC, select "Recovery mode" in boot-manager (GRUB) and then go for "root shell" option (you might need to press the DOWN arrow a couple of times). 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```

then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.

Did that and it reboot to the ubuntu.No blank screen.I still wanted to fix the fan speed.And and went and install again the Ati opensource from System>administration>hardware and select the Ati driver reboot.

This time , I get blank screen again.did the same thing uninstall suing 
```
sudo apt-get remove xorg-driver-fglrx
``` and now back without any ati driver.

The fan speed running at 100% is very annoying.Anyway to resolve it ?

---

### Post by ubfu on 2009-06-11
Now I am following this installation guide again 

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method)

Hope it helps

---

### Post by ubfu on 2009-06-11
Solve :D

Follow the link and it solve

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method)

and 

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_Driver_Manually)

---

