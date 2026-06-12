---
title: "Ndiswrapper"
date: 2008-12-15
forum: General Help
---

### Post by nilsk123 on 2008-12-15
EDIT:

Managed to fix it, thanks for reading anyway!

---

### Post by Titan8990 on 2008-12-15
This is the package you are looking for:


sudo apt-get install ndiswrapper-util-1.9

---

### Post by Ayuthia on 2008-12-15
If you don't have a working internet connection, but have the install CD, you can get the package from the CD:
```
sudo apt-cdrom add
```Insert the CD when asked.  Then:
```
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```

---

### Post by TIMMay333 on 2008-12-15
If you want to go the non-terminal way, if you go to Applications -> add/remove and search for windows wireless drivers, the ndiswrapper should be there.

---

### Post by nilsk123 on 2008-12-15
Thanks for the help, was able to find the desired packages after adding cdrom as a software source! So installed ndiswrapper and the desired driver, and it worked perfectly. After that I downloaded the nvidia display driver for my 8800 and after that I could enable the graphical effects, everything was perfect and working great.

But... ( theres allways a but )

Now that I've rebooted into windows xp, and then rebooted into ubuntu again, everything has gone wrong. The nvidia display driver is no longer enabled and therefor the effects dont work either.

For some reason the network driver doesnt work anymore either. Ndiswrapper -l still lists it as being installed and the device being present, but ubuntu doesnt seem to notice it anymore so I once again don't have a network connection.

What could be the problem here?

---

### Post by Ayuthia on 2008-12-15
You might check:
```
lsmod |grep -e ndiswrapper -e nvidia
```
and see if the modules are loaded for them.  If they are both present, you will need to check:
[codde]sudo cat /var/log/xorg.0.log|less[/code]to see if there are any error/warning messages for nvidia and for ndiswrapper check:
```
dmesg|grep ndiswrapper
```

If ndiswrapper is not loaded, you will need to load it by:
```
sudo modprobe ndiswrapper
```and you will need to check if ndiswrapper is being loaded at boot time:
```
cat /etc/modules|grep ndiswrapper
```If nothing returns:
```
echo ndiswrapper|sudo tee -a /etc/modules
```will add it for you.

---

### Post by nilsk123 on 2008-12-15
Ayuthia,

thanks a lot, heres my roundup:

nils@nils-desktop:~$ lsmod |grep -e ndiswrapper -e nvdia
ndiswrapper           196380  0 
usbcore               148848  8 ndiswrapper,usblp,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd

nils@nils-desktop:~$ dmesg|grep ndiswrapper
[   20.186539] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   20.483496] ndiswrapper: driver net5523 (,02/23/2006,1.5.0.110) loaded
[   20.484331] ndiswrapper (ZwQueryValueKey:2330): not fully implemented (yet)
[   21.188709] usbcore: registered new interface driver ndiswrapper

Sudo modprobe ndiswrapper immediatly initialsed my network adapter and it worked! Even after restart!

nils@nils-desktop:~$ cat /etc/modules|grep ndiswrapper
ndiswrapper


and I did the echo thing to add to modules, which I guess took care of the restart issue.

My nvidia is still out though I guess, trying to enable normal or extra effects gives me "Desktop effects could not be enabled".

Any thoughts on that?

---

### Post by nilsk123 on 2008-12-17
Did some further research, found the following in my log:

[IMG]http://img72.imageshack.us/img72/2724/nvidialogae7.png[/IMG]

---

