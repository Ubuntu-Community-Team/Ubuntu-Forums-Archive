---
title: "How do I get rid of an apps I don't want."
date: 2009-05-01
forum: Desktop Environments
---

### Post by irv on 2009-05-01
I have been trying to remove wicd from my laptop with not much luck. I want to remove wicd and install network-manager-gnome again. here is what I get:
> irv@irv-old-laptop:~$ sudo apt-get remove wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot libnm-util1 dkms fglrx-kernel-source
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  wicd
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1905kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 270048 files and directories currently installed.)
[COLOR="Red"]Removing wicd ...
Stopping wicd daemon...
invoke-rc.d: initscript wicd, action "stop" failed.
dpkg: error processing wicd (--remove):
 subprocess pre-removal script returned error exit status 1
update-rc.d: warning: /etc/init.d/wicd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Stopping any running daemons...
Starting wicd daemon...
Errors were encountered while processing:
 wicd
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
Any idea how to do this. Right now I have no network-manager showing up in my System>Administration. I can't change my network setting.
I went to [http://wiki.debian.org/LSBInitScripts]("http://wiki.debian.org/LSBInitScripts")
but I am not sure what it is telling me to do?
any help would be great. thanks

---

### Post by KhurramM on 2009-05-01
Try:


sudo dpkg -r wicd

OR

sudo dpkg -P wicd

U can see details in man dpkg.

Hope this helps u out.

---

### Post by irv on 2009-05-01
> **KhurramM said:**
> Try:


sudo dpkg -r wicd

OR

sudo dpkg -P wicd

U can see details in man dpkg.

Hope this helps u out.

I tried them both here's what I got:
sudo dpkg -r wicd
> irv@irv-old-laptop:~$ sudo dpkg -r wicd
[sudo] password for irv: 
(Reading database ... 284789 files and directories currently installed.)
Removing wicd ...
Stopping wicd daemon...
invoke-rc.d: initscript wicd, action "stop" failed.
dpkg: error processing wicd (--remove):
 subprocess pre-removal script returned error exit status 1
update-rc.d: warning: /etc/init.d/wicd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Stopping any running daemons...
Starting wicd daemon...
Errors were encountered while processing:
 wicd
irv@irv-old-laptop:~$ 

sudo dpkg -P wicd
> irv@irv-old-laptop:~$ sudo dpkg -P wicd
[sudo] password for irv: 
(Reading database ... 284789 files and directories currently installed.)
Removing wicd ...
Stopping wicd daemon...
invoke-rc.d: initscript wicd, action "stop" failed.
dpkg: error processing wicd (--purge):
 subprocess pre-removal script returned error exit status 1
update-rc.d: warning: /etc/init.d/wicd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Stopping any running daemons...
Starting wicd daemon...
Errors were encountered while processing:
 wicd
irv@irv-old-laptop:~$ 
Thanks for the suggestions

---

### Post by irv on 2009-05-02
I still have not got this problem solved. Is there any help on this? Thanks

---

### Post by zeex on 2009-05-02
> **irv said:**
> I still have not got this problem solved. Is there any help on this? Thanks

Hi, 

Try this 

```
$ sudo apt-get --purge remove wicd
```

Good luck  :)

---

### Post by irv on 2009-05-02
> **zeex said:**
> Hi, 

Try this 

```
$ sudo apt-get --purge remove wicd
```

Good luck  :)

I tried it and got:
> irv@irv-old-laptop:~$ $ sudo apt-get --purge remove wicd
bash: $: command not found
irv@irv-old-laptop:~$ 

Then I tried this [COLOR="Navy"]sudo dpkg -r wicd -- purge --force-all[/COLOR] and got:
> irv@irv-old-laptop:~$ sudo dpkg -r wicd -- purge --force-all
[sudo] password for irv: 
dpkg: status database area is locked by another process
irv@irv-old-laptop:~$ sudo dpkg -r wicd -- purge --force-all
(Reading database ... 284791 files and directories currently installed.)
Removing wicd ...
Stopping wicd daemon...
invoke-rc.d: initscript wicd, action "stop" failed.
dpkg: error processing wicd (--remove):
 subprocess pre-removal script returned error exit status 1
update-rc.d: warning: /etc/init.d/wicd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Stopping any running daemons...
Starting wicd daemon...
dpkg - warning: ignoring request to remove -- which isn't installed.
dpkg - warning: ignoring request to remove purge which isn't installed.
dpkg - warning: ignoring request to remove --force-all which isn't installed.
Errors were encountered while processing:
 wicd
irv@irv-old-laptop:~$ 


---

### Post by llemm on 2009-05-02
> **irv said:**
> I have been trying to remove wicd from my laptop with not much luck. I want to remove wicd and install network-manager-gnome again. here is what I get:

Any idea how to do this. Right now I have no network-manager showing up in my System>Administration. I can't change my network setting.
I went to [http://wiki.debian.org/LSBInitScripts]("http://wiki.debian.org/LSBInitScripts")
but I am not sure what it is telling me to do?
any help would be great. thanks

sudo apt-get remove --purge (app you want to remove>

---

### Post by irv on 2009-05-02
> **llemm said:**
> sudo apt-get remove --purge (app you want to remove>

If you look at my first post this is what I tried. Thanks any way.

---

