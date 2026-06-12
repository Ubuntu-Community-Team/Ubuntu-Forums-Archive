---
title: "Setting up Ubuntu Desktop - is this normal??"
date: 2007-05-23
forum: Desktop Environments
---

### Post by dpcamp on 2007-05-23
I installed Ubuntu Server, then decided that a GUI interface would make life a bit easier for me. I've been trying to get Ubuntu-desktop working but when i run sudo aptitude install ubuntu-desktop at the end I get this error
```
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 gnome-power-manager
 gnome-session

```
does that usually happen?

---

### Post by blazercist on 2007-05-23
thats not good looks like ur missing some of the required packages. there should be some how-to's on this type of this in the forum, try looking around I think you need a few more things than just ubuntu-desktop before you can do that.

You can try installing those packages that it listed at the end there before you attempt to install ubuntu-desktop that should help.

---

### Post by bernied on 2007-05-23
No, it doesn't usually happen, but you are trying to install power management utilities on a running system, so it is maybe not so unfeasable.
The packages are not missing, just not yet configured.

If it were mine, I'd restart the machine, then:
```
apt-get -f install
```
That will attempt to fix all packages that are not fully installed.

If that doesn't work,

The first error, from which all the others derive, is about acpid:
> initscript acpid, action "start" failed.
So the next thing to do is to see whether acpid is running or not, maybe stop it if it is, and start it if it isn't.

---

### Post by dpcamp on 2007-05-23
apt-get install is what generates the error as well.. I'm assuming I'm missing something, and starting to think installing the server edition wasn't a good idea.. I'll search around to see if I can find the how-to, if anyone knows where its at please post a link! haha 
thanks!

---

### Post by blazercist on 2007-05-23
Try:

After you install the server version, you can install X and a window manager. For instance:
sudo apt-get install xubuntu-desktop 
will install xfce, 

sudo apt-get install kubuntu-desktop 
will install kde, 

sudo apt-get install ubuntu-desktop 
will install gnome.

---

### Post by dpcamp on 2007-05-23
I ran sudo aptitude install ubuntu-desktop is that the problem?

---

### Post by DigitalAxis on 2007-05-23
It looks like all your errors are related to acpid not being configured properly, so that nothing related to power management is configured properly.

Try **sudo dpkg --configure acpid**.  That might help.

---

### Post by dpcamp on 2007-05-23
ok. I removed my ubuntu-desktop
then reinstalled it using apt-get install instead of aptitude install
acpi was still giving me problems
I stopped the service then ran sudo dpkg --configure acpid

this is what it gave me
```
Setting up acpid (1.0.4-5ubuntu6) ...
 * Loading ACPI modules...                                               [ OK ]
 * Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: Device or resource busy
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 acpid

```

---

### Post by yage on 2007-05-23
try sudo dpkg-reconfigure -a 
and then try to install the packages again

---

### Post by dpcamp on 2007-05-24
when I run dpkg-reconfigure all -a, when it asks me about enabling shadow password it gives me this error
```
delete line 'sysadmin:x:1000:1000:System Admin,,,:/var/www:/bin/bash'? duplicate password entry
delete line 'sysadmin:x:1000:1000:System Admin,,,:/var/www:/bin/bash'? duplicate password entry
delete line 'sysadmin:x:1000:1000:System Admin,,,:/var/www:/bin/bash'? duplicate password entry
delete line 'sysadmin:x:1000:1000:System Admin,,,:/var/www:/bin/bash'? duplicate password entry
delete line 'sysadmin:x:1000:1000:System Admin,,,:/var/www:/bin/bash'? duplicate password entry
delete line 'sysadmin:x:1000:1000:System Admin,,,:/var/www:/bin/bash'? pwck: no changes
Please correct the error and rerun `/sbin/shadowconfig on'

```
and then it kicks me back to the command line. Is that OK?

---

### Post by az on 2007-05-24
The server kernel may not make proper use of your hardware.  To use desktop hardware, you need the desktop (generic) kernel.

sudo apt-get install linux-generic

and then reboot.

You may not be able to do that if apt is tied into a knot.  You would maybe need to temporatily remove acpid

sudo dpkg -r acpid

EDIT:  Since shodow passwords were not even properly configured, your install never completed.  (probably because of acpid)  If you have not started to use your system you are better off to start from scratch using the live cd.  You can install the LAMP stack easily in Edgy and Fiesty using synaptic (install the lamp task) or by running tasksel.  In Dapper, tasksel in not installed by default.

---

### Post by dpcamp on 2007-05-24
yeah I had a feeling that was going to be the outcome of this.. I'm downloading desktop now and just going to install LAMP on it. Thanks guys!

---

