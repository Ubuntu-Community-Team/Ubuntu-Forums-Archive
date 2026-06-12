---
title: "VMWare Player fails to install"
date: 2006-08-31
forum: Desktop Environments
---

### Post by paulgami on 2006-08-31
This is a fresh install of Dapper on a Dell Latitude C840 laptop.  All I did was install ubuntu, update and then attempt to install vmware player.  It installed a couple of other vmware packages, which I assume caused the "file exists" errors.  Anyway, any ideas?

```
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.45.0/255.255.255.0 appears to be unused.

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


The subnet 192.168.20.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]
The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]


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

The subnet 192.168.183.0/255.255.255.0 appears to be unused.

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

The subnet 192.168.26.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1


```

---

### Post by haz2a on 2006-09-02
I had a similar problem and couldn't get the Ubuntu packages to install, so I installed the slightly later tarball from [www.vmware.com/products/player/](www.vmware.com/products/player/) instead.

Download the tarball into a tmp dir. 
Enter a root shell (eg: [FONT="Lucida Console"]$ sudo -i[/FONT])
Unpack the tarball: ```
# tar zxf VMware*tar.gz
```

Ensure All Correct Packages Installed for Compiling VM Modules
Check that the kernel headers matching the running kernel (uname) are installed.
Check that 'make' is installed.
Check that the version of gcc installed is the same as used to compile the kernel:-
```
cat /proc/version
```  

Check that there is a link '/usr/bin/gcc' pointing to the required version. If not, create it, eg:-
```
ln -s /usr/bin/gcc-4.0 /usr/bin/gcc
```  

Run the Install Script
```
# cd vmware-play* 
# ./vmware-install.pl
```  
If the script complains "previous installation has been detected ... Execution aborted" then:-
1. Check via Synaptic if any vmware packages are currently installed. If any are, they must be removed completely (including config files).  If they were not installed with synaptic, try running the script vmware-uninstall.pl (might have to find it first, if it exists).
2. Check that the dir /etc/vmware does not exist. If it does, remove it.
3. Search for any other 'vmware' files:  [FONT="Lucida Console"]find / -name *vmware*[/FONT]  
and delete them (except the new download and files extracted from it!)

Accept the default dirs (creating where necessary) for:-
binary files: /usr/bin
init dir: /etc
init scripts:  /etc/init.d 
libs: /usr/lib/vmware
docs: /usr/share/doc/vmware 
run vmware-config.pl? > y
EULA > y
Accept the default directories for:-
mime type icons: /usr/share/icons
desktop menu entries: /usr/share/applications
application icons: /usr/share/pixmaps

If the pre-built modules don't match kernel
(pre-built modules prob just i386 flavour of not-latest release) will ask if should build module vmon > yes
Location of kernel headers - /lib/modules/2.6.15-26-k7/build/include? > y
Should then build the module and confirm that "the module loads perfectly".

Networking for VMs? > y
NAT? > y
Probe for unused private subnet? > y
```
vmnet8 is a NAT network on subnet xxx.xxx.xxx.xxx
```
configure another? > n

Host-only networking? > y 
Probe for unused subnet? > y
```
vmnet1 is a host-only network on subnet xxx.xxx.xxx.xxx
```
configure another? > n

make ... building modules ...

```
MODPOST
Warning: Could not open /tmp/vmware-config1/vmnet-only/includeCheck.h: Invalid argument
```
- suspect this is not important
...

The module loads perfectly in the running kernel
Enable the Google searchbar? > n (default)
...

The configuration of VM Player 1.0.2 build-29634 ... completed successfully.
 
HTH
haz

---

