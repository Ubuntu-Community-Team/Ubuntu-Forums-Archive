---
title: "Brother Printer Driver Install Broke My Ubuntu 8.10 System"
date: 2008-12-18
forum: General Help
---

### Post by landrand on 2008-12-18
I've been having problems with my printer using Ubuntu 8.10.  I have a Brother HL-1440 laser printer attached to a usb port.  The printer will work fine for a couple of jobs then it will report the following error. "Printer Brother HL-1440" may not be connected" in an icon on the upper right hand corner of my desktop.  To get it to work, I'll go over the printer and unplug the USB cable and then reconnect the cable.  This doesn't always work, but it usually does. Anyway, I thought I'd try to see if the problem was a driver issue.  I went to the Brother web site where I download the drivers for the printer and followed the install directions as shown here. 
[http://solutions.brother.com/linux/en_us/instruction_prn1a.html](http://solutions.brother.com/linux/en_us/instruction_prn1a.html)  

I had problems using the first command sequence shown below. 

# dpkg  -i  --force-all  --force-architecture  hl1440lpr-1.1.2-1.i386.deb 

I don't think this installed correctly as I received errors after issuing the command.

root@mythfe1:/home/lind/Desktop# dpkg  -i  --force-all  --force-architecture hl1440lpr-1.1.2-1.i386.deb 
(Reading database ... 122076 files and directories currently installed.)
Preparing to replace hl1440lpr 1.1.2-1 (using hl1440lpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl1440lpr ...
/var/lib/dpkg/info/hl1440lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing hl1440lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1440lpr-1.1.2-1.i386.deb


I think this one installed correctly

# dpkg  -i  --force-all  --force-architecture  cupswrapperHL1440-1.0.2-1.i386.deb

Since the hl1440lpr-1.1.2.1 driver didn't install correctly, I'm now getting the following errors when I try to install other packages.  I can't install anything else until this is fixed. For example, I'd like to install opera.  Here's what I get when I try to install it.

root@mythfe1:/home/lind/Desktop# aptitude install opera
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for opera
No candidate version found for opera
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the hl1440lpr package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the hl1440lpr package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

Here's what I get when I try to remove the hl1440lpr application:

root@mythfe1:/home/lind/Desktop# dpkg  -r  --force-all  --force-architecture hl1440lpr
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 122075 files and directories currently installed.)
Removing hl1440lpr ...
/var/lib/dpkg/info/hl1440lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing hl1440lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1440lpr

Any ideas?  I think trying to fix my printer problem I've created a much bigger problem.  Apparently, trying to install this Brother printer driver has made my system unable to install other software.  Any help would be greatly appreciated.

---

### Post by Polygon on 2008-12-18
well there is your first problem, you forced dpkg to install that package, which is what broke it

can you remove teh two packages that you installed?

try running 

sudo apt-get -f install

after you remove the two packages you install and see if that fixes it, if not, dpkg seems to be borked and reinstall might be your only option :O

---

### Post by landrand on 2008-12-18
Here's what I get when I try your suggested commands. Didn't work.  I certainly hope I don't have to reinstall ubuntu.  What a pain that would be.


root@mythfe1:/home/lind/Desktop# apt-get -f install ./hl1440lpr-1.1.2-1.i386.deb 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hl1440lpr needs to be reinstalled, but I can't find an archive for it.

root@mythfe1:/home/lind/Desktop# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hl1440lpr needs to be reinstalled, but I can't find an archive for it.

---

### Post by plucky on 2008-12-18
Did you actually do all the pre-required procedures?

```
# Pre-required Procedure (2)
    Related distributions
    Ubuntu 8.04/8.04.1, Ubuntu 8.10
    Related products/drivers
    cupswrapper printer/PC-FAX drivers
    Requirement
    1. "sudo aa-complain cupsd" command is required before the installation.
    2. "sudo mkdir /usr/share/cups/model" command is required before the installation. 
```

   ```
 Requirement (superuser authorization is required to run the command) 
    Creating a symbolic link is required before the installation
    For Debian based distributions except Ubuntu 8.10: "ln -s /etc/init.d/cupsys /etc/init.d/lpd"
    For Redhat based distributions and Ubuntu8.10: "ln -s /etc/init.d/cups /etc/init.d/lpd" 
```

try to remove the package ```
sudo dpkg -r hl1440lpr-1.1.2-1.i386.deb 
```

or ```
sudo apt-get install -f
``` just that command without the name of the file.


After that use the **Synaptic Package Manager** and search for **hl-1440** and install the "lpr" and "cupswrapper" drivers for that printer.


Good Luck


@Polygon

Please read [this](http://ubuntuforums.org/showthread.php?t=1010875)

---

### Post by landrand on 2008-12-22
Looks like I didn't create the link.  I did the ln command and I was able to install the brother drivers.  Thanks.

 As I stated in my original post, my system often reports that the printer may not be connected.  I'll see how well the usb printer now works after installing these drivers.

---

