---
title: "Network MFC Scanner problem"
date: 2009-02-11
forum: General Help
---

### Post by smi402 on 2009-02-11
I have studied the many threads related to xsane scanning problems, but have not been able to solve my particular problem.

I have a LAN with a Brother MFC-8460N connected directly to it via an ethernet cable with a static address of 192.168.1.253. The network also has a MacBook OSX Leopard, A WinXP and three Ubuntu Intrepid 64bit machines on it. All machines, including the Ubuntu machines, access the printer function of the MFC without any problems. However the Ubuntu Intrepid machines are having problems accessing the scanner function of the MFC. They will recognize the device and run a scan when run as sudo but not as an ordinary user so I suspect a permissions problem, but I do need your help in locating that.

sane, sane-utils, xsane and their dependencies were installed via Synaptic. The latest 64 bit versons of brscan2 and brscan-skey .deb packages were downloaded from the Brother site and installed with dpkg.

brsaneconfig2 -a name=SCANNER model=MFC-8460N ip=192.168.1.253 was run and shows the device is registered at the correct IP address.
```
frank@FWS:~$ brsaneconfig2 -q | grep SCANNER
  0 SCANNER             "MFC-8460N"         I:192.168.1.253
```
The 192.168.1.253 responds to pings and, as I said, I can print from the device as any user.
Running scanimage as sudo yields the expected outcome and sudo xsane finds the scanner and allows scanning.
```
frank@FWS:~$ sudo scanimage -L
[sudo] password for frank: 
device `brother2:net1;dev0' is a Brother MFC-8460N SCANNER
```
However, when run as user frank scanimage produces a Segmentation fault:
```
frank@FWS:~$ scanimage -L
Segmentation fault

```
User frank is a member of the scanner group.

Any assistance or thoughts would be greatly appreciated as I need to get this problem solved in order to scan some images into GIMP.

Frank

---

### Post by smi402 on 2009-02-12
More Information!!

I had a partition with Ubuntu 7.10 32bit on one of the network machines so I installed the scanner function software using the instructions from Brother:

[http://solutions.brother.com/linux/sol/printer/linux/sane_install-net.html](http://solutions.brother.com/linux/sol/printer/linux/sane_install-net.html)

The scanner function works perfectly when run as either sudo or a normal user under Ubuntu 7.10. However, as pointed out in my earlier post, under Intrepid 8.10 (64bit) on a different machine I can only use the scanner as sudo - using it as an ordinary user produces a segmentation fault error. I am clearly missing some simple detail required for the Intrepid installation - any advice about this would be greatly appreciated.

Frank

---

### Post by smi402 on 2009-02-16
BUMP!

Can anyone offer any advice on getting this scanner to work through a normal user rather than through sudo under Intrepid 8.10?

Frank

---

### Post by hyper_ch on 2009-02-16
wouldn't it be simplre if you initiate the scan on the printer and the printer send then the document per ftp to your ocmputer?

---

