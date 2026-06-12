---
title: "vmware player - Will not complete install now cant reinstall or uninstall"
date: 2006-09-30
forum: Desktop Environments
---

### Post by djrosen on 2006-09-30
Hello all, I recently installed Dapper and loving it, moved from Hoary which I also loved, but I digress.

I used Automatix immidiately after installation to add some things, after which I updated the whole system as requested by the auto update. Everything during the installation of the various sundry items seems to have gone well with the exception of vmware-player. Now any use of apt-get/synaptic/aptitude attmepts to 'fix' the install of the vmware player. Below is the error:

The below is displayed everytime I attempt to install anything via synaptic/apt-get/aptitude. Anything I intended to install seems to install fine.

```

Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.50.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes] n

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes] n

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes] n

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists.  Overwrite? [yes] n

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.87.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes] n

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes] n

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes] n

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
Bridged networking on /dev/vmnet0	                               done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gkrellm-common (2.2.7-5ubuntu1) ...
...
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


```

it never recovers and I have to now interact with every installation via the above. I have tried answering yes to replace the files, no change.

I had also installed inedt with the inclination to get leafnode up and running but I have done no furhter config of that daemon, just in case that is pertinent in some way.

Thanks for any suggestions as ](*,)

-- 
David

---

### Post by dad311 on 2006-09-30
I also had this problem.  I removed vmplayer using the package manager and then removed the /etc/vmware directory.  After the removal, I used the howto [http://doc.gwos.org/index.php/VMWareXP](http://doc.gwos.org/index.php/VMWareXP) to install the vmware server.

---

### Post by djrosen on 2006-09-30
> **dad311 said:**
> I also had this problem.  I removed vmplayer using the package manager and then removed the /etc/vmware directory.  After the removal, I used the howto [http://doc.gwos.org/index.php/VMWareXP](http://doc.gwos.org/index.php/VMWareXP) to install the vmware server.

The un/re/install via package manager failed. I did however find a resolution in the forums that led me to the below solution. It appears that the vmware-player and associated modules that are available in the repositories conflict with the latest kernel update in the repositories.

To resolve, I rebooted with the old kernel (glad I left it in the grub config) and then synaptic was sucsessful at removing the player. I then removed the kernel modules and all now seems well. Thanks for the info.

-- 
David

---

