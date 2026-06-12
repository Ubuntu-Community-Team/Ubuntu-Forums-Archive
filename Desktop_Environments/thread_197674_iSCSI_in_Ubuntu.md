---
title: "iSCSI in Ubuntu"
date: 2006-06-16
forum: Desktop Environments
---

### Post by longinus on 2006-06-16
Has anyone got an iscsi initiator to compile on Ubuntu? Or perhaps on some other distro?

I tried different versions of linux-iscsi and open-iscsi, but none of them worked. Since I don't usually compile stuff, I can't find out the problem. The path to the kernel src is right. Perhaps its because of some warnins, and the msg in the beginning "cc1: warnings being treated as errors" ?

It compiles some of the drivers, and when trying to compile one called "iscsi-ioctl" it gives warnings like "implicit declaration of function ‘class_simple_device_add’". In the end it probably can't compile the driver, and gives and error and leaves. :-( 

Any help would be appreciated.
Thanks.

---

### Post by longinus on 2006-06-16
I found something about open-iscsi and ubuntu..
[http://revu.tauware.de/details.py?upid=2204](http://revu.tauware.de/details.py?upid=2204)

But I don't know what this is... some kernel patches? ::rolleyes:

---

### Post by neekofab on 2006-08-10
(done in Ubuntu Server i386)
apt-get install linux-headers-amd64-server build-essential libdb4.3-dev
wget [http://www.open-iscsi.org/bits/open-iscsi-1.0-485.tar.gz](http://www.open-iscsi.org/bits/open-iscsi-1.0-485.tar.gz)
tar zxf open-iscsi-1.0-485.tar.gz
cd open-iscsi-1.0-485
patch -p1 < kernel/2.6.14-and-2.6.15-compat.patch
make install

(in my installation the iSCSI components are on a different network)
vi /etc/network/interfaces
 auto eth0:0
 iface eth0:0 inet static
 address iSCSI_initiator_IP
 netmask iSCSI_initiator_NETMASK
 broadcast iSCSI_initiator_BROADCAST
 gateway iSCSI_initiator_GATEWAY

vi /etc/initiatorname.iscsi
 InitiatorName=iqn.iSCSI_initiator_NAME
mkdir -p /var/db/iscsi
/etc/init.d/open-iscsi start
iscsiadm -m discovery --type=sendtargets --portal=iSCSI_target_IP
iscsiadm -m node --record=iSCSI_target_RECORD-SHORTNAME -login
 SCSI_target_RECORD-SHORTNAME is the bit in []'s from the discovery sendtargets command
dmesg should now register a new scsi device.

Later I'll post a guide for combining all this with vmware-server and redhat-cluster-service (using gfs)

---

### Post by longinus on 2006-08-10
Humm, this looks good! I didn't try to apply any kernel patchs, but it seems easy enough.. I'll try it later.

It would be nice to have a good tutorial on iSCSI initiator and server, since I really hate using a windows machine to host my iscsi targets.

---

### Post by neekofab on 2006-08-11
> **longinus said:**
> Humm, this looks good! I didn't try to apply any kernel patchs, but it seems easy enough.. I'll try it later.

It would be nice to have a good tutorial on iSCSI initiator and server, since I really hate using a windows machine to host my iscsi targets.

the patch is not some kernel patch, it's in the open-iscsi tarbal and is applied to the open-iscsi source to fix it based on which kernel version you are running.

I still have some notes to post to enable auto login of the initiator.... more to come

---

### Post by neekofab on 2006-08-11
> **neekofab said:**
> the patch is not some kernel patch, it's in the open-iscsi tarbal and is applied to the open-iscsi source to fix it based on which kernel version you are running.

I still have some notes to post to enable auto login of the initiator.... more to come

Open-iSCSI (Software iSCSI initiator) on a Ubuntu Server Redhat-Cluster-Suite node

1.apt get install libdb4.3-dev
2.wget [http://www.open-iscsi.org/bits/open-iscsi-1.0-485.tar.gz](http://www.open-iscsi.org/bits/open-iscsi-1.0-485.tar.gz)
3.tar zxf open-iscsi-1.0-485.tar.gz
4.cd open-iscsi-1.0-485
5.patch -p1 < kernel/2.6.14-and-2.6.15-compat.patch
6.make install
7.vi /etc/network/interfaces
	auto eth0:0
iface eth0:0 inet static
address iSCSI_initiator_IP
netmask iSCSI_initiator_NETMASK
broadcast iSCSI_initiator_BROADCAST
gateway iSCSI_initiator_GATEWAY
8.vi /etc/initiatorname.iscsi
InitiatorName=iqn.iSCSI_initiator_NAME
9.mkdir -p /var/db/iscsi
10.update-rc.d open-iscsi start 41 S . start 34 0 6 . (for correct shutdown using redhat-cluster-suite: update-rc.d open-iscsi start 41 S . start 03 0 6 .)
11.vi /etc/init.d/open-iscsi (enable auto login)
add  after line "DAEMON=/usr/sbin/iscsid"
ISCSIADM=/usr/sbin/iscsiadm

add in "iscsid_start()" function after line "start-stop-daemon --start --exec $DAEMON --quiet"


        {       TARGETS=$($ISCSIADM -m node | sed 's@\[\(.*\)\] .*@\1@g')
                for rec in $TARGETS; do
                STARTUP=`$ISCSIADM -m node -r $rec | grep "node.conn\[0\].startup" | cut -d' ' -f3`
                NODE=`$ISCSIADM -m node -r $rec | grep "node.name" | cut -d' ' -f3`
                if [ $STARTUP = "automatic" ] ; then
                        echo -n "Logging into $NODE: "
                        $ISCSIADM -m node -r $rec -l
                fi
                done
        }

add in "iscsid_stop()" function after first line "{"


        {       TARGETS=$($ISCSIADM -m session | sed 's@\[[^:]*:\(.*\)\] .*@\1@g')
                for rec in $TARGETS; do
                        NODE=`$ISCSIADM -m node -r $rec | grep "node.name" | cut -d' ' -f3`
                        if $ISCSIADM -m node --record $rec --logout ; then
                        echo -n "Logging out from $NODE: "
                        else
                                echo "Logout failed"
                        fi
                        done
        }
12./etc/init.d/open-iscsi start
13.iscsiadm -m discovery --type=sendtargets --portal=iSCSI_target_IP
14.iscsiadm -m node --record= iSCSI_target_RECORD-SHORTNAME  --op=update --name=node.startup &#8211;value=automatic
15./etc/init.d/open-iscsi restart

---

### Post by TonioRoffo on 2006-09-17
@neekofab,

This does not work for me, I get all kinds of compilation errors, I tried in 3 different machines.

Perhaps there's more dependencies than you posted?

Thanks

---

### Post by TonioRoffo on 2006-09-17
OK, I got it working on 2.6-15-26

However my production servers are at 2.6.15-23 - make runs fine, but "make install" yields errors.

Edit: This is confirmed:

* Tried a clean 2.6.15-23-server and failed.
* Upgraded kernel to 2.6.15-26-server, and succeeded!

Next I'll try the auto-login

---

### Post by Widodh on 2006-10-23
Please take a look at: [http://ubuntuforums.org/showthread.php?t=236825](http://ubuntuforums.org/showthread.php?t=236825)

---

### Post by Dirk_DC on 2007-07-17
I followed neekofab's instructions and managed to get this working in Ubuntu 6.06 LTS using a 2.6.15 kernel.
I had some problems with step 14 however, for it to work I had to madify it to read:
14.iscsiadm -m node --record= iSCSI_target_RECORD-SHORTNAME --op=update --name=node.conn[0].startup –value=automatic

Otherwise the LUN did not get mounted.

Regards,
Dirk

---

### Post by jnelson76 on 2007-10-10
Can't seem to run step 14, keep getting "iscsiadm: can not set parameter"

---

### Post by neekofab on 2007-11-20
instead of 13 & 14, try the following:

iscsiadm -m discovery --type=sendtargets --portal=iSCSI_target_IP
iscsiadm --mode node --targetname iSCSI_target_RECORD-SHORTNAME --portal=iSCSI_target_IP:3260 --login
iscsiadm --mode node --targetname iSCSI_target_RECORD-SHORTNAME --portal=iSCSI_target_IP:3260 -o update -n node.startup -v automatic

--Neekofab

---

