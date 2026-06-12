---
title: "[SOLVED] Scanner Not Found after upgrade to Intrepid Ibex"
date: 2008-12-29
forum: General Help
---

### Post by VinitAdhopia on 2008-12-29
Hello,

I recently upgraded from Ubuntu 8.04 to 8.10.  In doing so, my scanner is no longer functioning properly.

I am using a Brother DCP-5440CN MFC.  It is not plugged directly into my machine via USB.  Instead, I set it up as a network printer/scanner, as I have a few other machines on my home network.

I can still print to the machine, I just can't scan.  The network scanning ability still works on the other machines on my network (not running Ubuntu) and the problem only appeared after I upgraded to Intrepid Ibex.  Specifically, while using gscan2pdf, I get a "Scanner Not Found" message.

I've already checked my user account under System -> Administration -> Users and Groups to ensure that I have the appropriate privileges to use scanners.

Also, using the Synaptic Package Manager, I double-checked to see that I have a Brother Scanner Driver installed as well as the following packages: sane, sane-utils, libsane, libsane-extras, xsane and xsane-common.

I tried using sane-find-scanner, but it returns without finding my scanner.

I've read other posts on the web mentioning having to create /etc/sane.d/epkowa.conf, but I don't know what this file should look like.

Has anyone else experienced this problem after upgrading to 8.10?  Any help would be greatly appreciated.

Thanks in advance.

---

### Post by plucky on 2008-12-29
Have you told the scanner driver where the scanner is on the network?

From the [Brother website](http://solutions.brother.com/linux/en_us/instruction_scn1b.html) this might help.

To check if driver is installed ```
dpkg  -l  |  grep  Brother
```

To confirm network scanner entry ```
brsaneconfig2  -q  |  grep  (name  of  your  device)
```


Good Luck

---

### Post by VinitAdhopia on 2008-12-29
Thanks for your reply.

I tried the commands you mentioned.
The driver is definitely installed.
```
dpkg -l | grep Brother
ii  brscan-skey                      0.2.1-1                  Brother Linux scanner S-KEY tool
ii  brscan2                          0.2.4                    Brother Scanner Driver
ii  dcp540cncupswrapper              1.0.1-1                  Brother CUPS Inkjet Printer Definitions
ii  dcp540cnlpr                      1.0.1-1                  Brother lpr Inkjet Printer Definitions

```

Also, I was able to confirm the network scanner entry.
```
brsaneconfig2 -q | grep DCP-540CN
 71 "DCP-540CN"
  0 SCANNER             "DCP-540CN"         I:192.168.1.102
```

Unfortunately, the problem persists.  I know that the IP address is correct because I am able to print to the device just fine.

I'm not really sure where else to look.  What else could I try?

---

### Post by pyromanic123boom on 2008-12-29
I had this same problem after I upgraded; I was using a Brother MFC7420. In fact, I had to fix CUPS first, then this.

First, I completely removed xsane, my image scanning program. Then I reinstalled the scanner driver from the brother linux driver page, and rebooted.

Then I reinstalled xsane, and it worked again. If there was anything else I remember that I did, I'll post, but I think that was it.

---

### Post by pyromanic123boom on 2008-12-29
I forgot:  you have to manually install the brother driver. Don't use synaptic for this.

Brother linux scanner drivers- [http://solutions.brother.com/linux/en_us/download_scn.html](http://solutions.brother.com/linux/en_us/download_scn.html)

---

### Post by plucky on 2008-12-29
> I'm not really sure where else to look. What else could I try? 

What does ```
scanimage -L
``` show.

Open a terminal and ```
ping -c 5 192.168.1.102
``` to see if you can communicate with your printer/scanner over the network.

You could also try to run xsane in super user mode to see if it could be a permissions problem.```
gksudo xsane
```
**It is not recommended to use super user mode in normal everyday activity,but is a legitimate troubleshooting tool.**

Good luck

---

### Post by VinitAdhopia on 2008-12-30
After uninstalling gscan2pdf and xsane, reinstalling the scanner driver and then re-installing xsane and gscan2pdf, my scanner is finally working again!  :D

Thanks for your help guys!

---

