---
title: "how to install VmWare tools"
date: 2009-03-16
forum: General Help
---

### Post by big136 on 2009-03-16
Hi,
I have created a XUBUNTU vm machine. I can see Vmware Tools as a CD icone on desktop. How can I install it ?
When in prompt I issue /usr/bin/vmware -toolbox ,
I receive :
No such a directory.
And in /media/cdrom i have :
VMwareTools-1.0.3-44356.i386.rpm

Thank you.

---

### Post by yeats on 2009-03-16
Go to the Devices menu, and there is an "Install Guest Additions" option.  Try that while your machine is booted up.

---

### Post by big136 on 2009-03-16
Thank you for reply. 
should I Go to the Devices menu of my XUBUNTU or VmWare ? Any way I can not see it anywhere.
Regards.

---

### Post by Cheesemill on 2009-03-16
Check out my post [here]("http://ubuntuforums.org/showthread.php?t=1094861") about installing VMware tools.

Cheesemill

---

### Post by yeats on 2009-03-16
Sorry - that's VirtualBox :oops:

Please disregard.

(Or try VirtualBox :-) )

---

### Post by big136 on 2009-03-16
thank you but when issued :
sudo vmware-tools-distrib/vmware-install.pl -d


I had :
Unable to copy the source file ./installer/services.sh to the destination file 
/etc/init.d/vmware-tools.
 and then when I gave chmod 777 to /etc/init.d/
and retried :
I had :
root@ak-xubuntu:/tmp# sudo vmware-tools-distrib/vmware-install.pl -d
A previous installation of VMware software has been detected.

Failure

Thank for help.

---

### Post by Cheesemill on 2009-03-16
The -d switch just means to install with all default options. Try running it without this switch and it should give you more detailed output. It will probably ask you if you want to remove the current version before re-installing.

Cheesemill

---

### Post by big136 on 2009-03-17
> **Cheesemill said:**
> The -d switch just means to install with all default options. Try running it without this switch and it should give you more detailed output. It will probably ask you if you want to remove the current version before re-installing.

Cheesemill

Thank you. Even without -d switch I receive :
sudo vmware-tools-distrib/vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

Thanks for help.

---

