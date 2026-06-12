---
title: "vmware player installtion failure"
date: 2006-07-20
forum: Desktop Environments
---

### Post by techrush on 2006-07-20
im running a fresh install of dapper wwith the latest 686-smp kernel. vmware fails to install from synapotic with the output from synaptic reading as follows

```
[Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.189.0/255.255.255.0 appears to be unused.

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.40.0/255.255.255.0 appears to be unused.

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.113.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists.  Overwrite? [yes]

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...


The subnet 172.16.120.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]
The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]


Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet
                                                                      failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player



```

any help resolving this issue would be greatly appreciated!

---

### Post by krismatth3 on 2006-07-20
What package did you install? "vmware-player"?

---

### Post by techrush on 2006-07-20
yes i was attempting to install the package "vmware-player".

---

### Post by techrush on 2006-07-20
i was able to successfully install vmware player using the tarball from vmware.com. not sure who the maintainer of the vmware-player .deb is or how i would report a bug to them but there is an issue with this package.

---

### Post by brentoboy on 2006-07-29
I noticed the same thing when I installed it from synaptic.

I also noticed that it installed an old 386 kernel, which it must have been built for.

it wont be able to load the module it needs to load until the kernel matches the module.  You need to reboot using the ........23-386 kernel instead the 26-686 kernel.

when I do that, I get passed the part where you are getting stuck.  but it still doesnt finish the install without complaining about NAT and Bridging which I think is an IPtables issue.

anyway, I think I an going to go for the source version that techrush pointed out.

---

### Post by giuliastro on 2006-08-01
I had the same problem, does anyone have an updated vmware-player deb?

---

### Post by giuliastro on 2006-08-04
To install correct modules for latest kernel versions you need to include security-multiverse repository. You will go thru the problems you are having but install will stop anyway by the end complaining it cannot find vmware-config.pl which is not included in deb package.

If someone has a quick fix for this please let me know.

---

### Post by thoolihan on 2006-08-08
I was able to install today.  Here's a quick summary of what worked:
```

sudo apt-get install linux-headers-2.6.15-26-386 
sudo apt-get install vmware-player-kernel-modules-2.6.15-26
sudo apt-get install vmware-player
sudo ln -sf /usr/lib/vmware/modules /usr/lib/vmware-player/
sudo vmware-config.pl
sudo rm -r /etc/vmware/not_configured

```
when prompted for the header path during vmware-config.pl specify 
/usr/src/linux-headers-2.6.15-26-386

Hope this helps...
Tim

---

### Post by pelle.k on 2006-08-12
This package royally sucks!
vmware-player is really the first real problem i've had in dapper.

---

### Post by seanf on 2006-09-18
For some reason, the vmware-player-kernel-modules-2.6.15-26 doesn't show up in synaptic on my system. I downloaded the deb from here:

[http://packages.ubuntu.com/dapper/misc/vmware-player-kernel-modules-2.6.15-26](http://packages.ubuntu.com/dapper/misc/vmware-player-kernel-modules-2.6.15-26)

Then I installed vmware-player and vmware-player-kernel-modules-2.6.15-23 from Synaptic - which of course failed, because of the kernel module.

I then installed the vmware-player-kernel-modules-2.6.15-26 deb with gdebi.

Then I reinstalled vmware-player with 'sudo apt-get install vmware-player' and it successfully installed.

---

### Post by sog on 2006-09-19
i'm having the same problem, and i can't remove the package either. now, everytime i apt-get install i have go through the failed config for the package, which is very suboptimal. 

any suggestions on how to eradicate the package?

---

### Post by tagra123 on 2006-09-19
This how to works with breezy and dapper:

[http://ubuntuforums.org/showthread.php?t=84275](http://ubuntuforums.org/showthread.php?t=84275)

---

### Post by sog on 2006-09-19
wish there was a howto for removal :(

---

### Post by tagra123 on 2006-09-19
installing using the How-to there is an uninstall script

---

### Post by rcatman on 2006-09-19
Don't download the player. Download vmware server.
Check this thread out, it worked like a charm for me. Absolutely no problems.

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

---

### Post by tagra123 on 2006-09-21
I installed vmware server and have to say I like it better than the player too.

---

### Post by sog on 2006-09-21
"installing using the How-to there is an uninstall script"

yeah, but i installed from apt. bad choice, in this case.

---

### Post by Stuky on 2006-09-29
Once I installed the linux-headers and vmware-player-kernel-modules to match my kernel version, vmware-player installed OK.

---

