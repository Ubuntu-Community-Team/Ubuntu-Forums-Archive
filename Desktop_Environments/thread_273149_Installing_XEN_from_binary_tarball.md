---
title: "Installing XEN from binary tarball"
date: 2006-10-07
forum: Desktop Environments
---

### Post by galego on 2006-10-07
was wondering if anyone out there has installed XEN on theur ubuntu, and if so do you have a real good how to or could you provide some guidance.

---

### Post by scoobyd00 on 2006-10-21
Hello,

There were my notes that enabled me to install a fully working XEN system from binary tarballs onto Ubuntu Dapper. Maybe they will help you.

> 

==========================================

apt-get install bridge-utils bzip2 debootstrap iproute libcurl3-dev make python python-twisted screen zlib1g-dev

apt-get remove ppp pppconfig pppoeconf

=======================================================================

mkdir xen ; cd xen

wget [http://bits.xensource.com/oss-xen/release/3.0.3-0/bin.tgz/xen-3.0.3_0-install-x86_32.tgz](http://bits.xensource.com/oss-xen/release/3.0.3-0/bin.tgz/xen-3.0.3_0-install-x86_32.tgz)

tar xzf xen-3.0.3_0-install-x86_32.tgz

cd dist

./install.sh

=======================================================================

cd /boot

mkinitramfs -o initrd.img-2.6.16.29-xen 2.6.16.29-xen 

ln -s initrd.img-2.6.16.29-xen initrd.img-2.6.16-xen

ln -s initrd.img-2.6.16-xen initrd.img-2.6-xen

=======================================================================

ln -s /usr/lib/libcrypto.so.0.9.7 /usr/lib/libcrypto.so.4

ln -s /usr/lib/libssl.so.0.9.7 /usr/lib/libssl.so.4

ln -s /usr/lib/libcurl.so.3.0.0 /usr/lib/libcurl.so.2

=======================================================================

update-rc.d xend defaults 20 21 

update-rc.d xendomains defaults 21 20

=======================================================================

nano /etc/init.d/xend

ADD NEAR TOP:

	## ensure /var/run/xenstored exists

	if [ ! -d /var/run/xenstored ] ; then

	  mkdir /var/run/xenstored

	fi

=======================================================================

nano /etc/init.d/xendomains

REPLACE:

	LOCKFILE=/var/lock/subsys/xendomains

WITH:

	LOCKFILE=/var/lock/xendomains

=======================================================================

nano grub/menu.lst

ADD ENTRY:

	title Xen 3.0.3 / Debian Linux 2.6.16
	kernel /xen-3.0.gz console=vga
	module /vmlinuz-2.6-xen root=/dev/md2 ro console=tty0
	module /initrd.img-2.6-xen
	savedefault
	boot

=======================================================================

reboot

=======================================================================

wget [http://xen-tools.org/software/xen-tools/xen-tools-2.7.tar.gz](http://xen-tools.org/software/xen-tools/xen-tools-2.7.tar.gz)

tar xzf xen-tools-2.7.tar.gz

cd xen-tools-2.7

nano ./Makefile

REPLACE:

	install: install-bin install-etc install-hooks install-manpages

WITH:

	install: install-bin install-etc install-hooks ### install-manpages

make install

=======================================================================

xen-create-image --debootstrap --dist=edgy --hostname=exporter1 --initrd=/boot/initrd.img-2.6-xen --ip=192.168.3.100 --kernel=/boot/vmlinuz-2.6-xen --lvm=exporter --mirror=http://gb.archive.ubuntu.com/ubuntu/ --size=1.5G --swap=200M

=======================================================================



:-D Jamie

---

### Post by scoobyd00 on 2006-10-21
Oh, and for the sake of completeness - these are my notes for Edgy Install via Apt...

> 
=======================================================================

apt-get install libc6-xen lvm-common lvm2 xen-hypervisor-3.0-i386 xen-image-xen0-2.6.17-6-generic-xen0 xen-tools xen-utils-3.0

=======================================================================

cd /boot

mkinitramfs -o initrd.img-2.6.17-6-generic-xen0 2.6.17-6-generic-xen0

mv xen0-linux-2.6.17-6-generic-xen0 vmlinuz-2.6.17-6-generic-xen0

=======================================================================

nano grub/menu.lst

ADD ENTRY:

title Xen 3.0.3 / Ubuntu Edgy (kernel 2.6.17)
kernel /xen-3.0-i386.gz console=vga
module /vmlinuz-2.6.17-6-generic-xen0 root=/dev/md2 ro console=tty0
module /initrd.img-2.6.17-6-generic-xen0
savedefault
boot

=======================================================================

reboot

=======================================================================

xen-create-image --debootstrap --dist=edgy --hostname=exporter1 --initrd=/boot/initrd.img-2.6-xen --ip=192.168.3.100 --kernel=/boot/vmlinuz-2.6-xen --lvm=exporter --mirror=http://gb.archive.ubuntu.com/ubuntu/ --size=1.5G --swap=200M

=======================================================================



:-D Jamie.

---

### Post by jgoor on 2006-11-01
When I follow this exact instructions for Edy (except for the 'lvm' - which I do not want to use), I cannot ping my DomU.
Reason: eth0 is down in DomU.

(in DomU) After '**ifup -a**' I get:

[B]SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.[/B]

My **/etc/network/interfaces**:

[B]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.61.111
        netmask 255.255.255.0
        broadcast 192.168.61.255
        gateway 192.168.61.2
[/B]

The rest seems Ok.
Any ideas?

---

### Post by aaahoopy on 2006-11-01
One additional thing I just noted about installing from the prebuilt tarballs: The scripts in /etc/xen/scripts were all using /bin/sh when they sometimes needed to use /bin/bash.  With /bin/sh being handled by dash in edgy this caused spectacular failues.  When I started a guest with xm, it would hang for a long time and come back with the vif could not be connected message.  Looking in /var/log/xen/xen-hotplug.log showed bad traps.  

I fixed the problem with the following:
cd /etc/xen/scripts
sed -i -e 's/\/bin\/sh/\/bin\/bash/g' `grep -l "/bin/sh" *`

EDIT: I am experiencing issues with the cdrom and I do not know if it is due to my solution not being quite right, or if it is due to some other issue.  Will find out what is happening and post my results here.
EDIT2: My issue with the CDROM was due to looking at old/new instructions and the fact the oldstyle cdrom support is gone.  Google for "New style CDROM config in Xen 3.0.3" for details.  Good luck everyone.

---

### Post by jgoor on 2006-11-02
Hi again!

After fiddling around I found that IMHO the howto of edgy lacks one thing: installation of bridge-utils.

What I did:
1) install bridge-utils
2) edit xend-config.sxp (replace 'dummy' with 'network-bridge')
3) restart xend
Now I got the xenbr0 and vif0.0 interfaces up.
After starting the DomU I immediately got an extra vif1.0 interface in Dom0 and I could ping the DomU.

*Now* I've got something *really* working!

Can someone please verify this?
Are these steps indeed missing from the howto by Jamie or am *I* missing something? Could it be done easier?
Let me know!
Thanx.

P.S.
Just to be as complete as possible, the DomU configuration:

#  -*- mode: python; -*-
kernel  = '/boot/vmlinuz-2.6.17-6-generic-xen0'
ramdisk = '/boot/initrd.img-2.6.17-6-generic-xen0'
memory  = '128'
root    = '/dev/hda1 ro'
disk    = [ 'file:/xen-images/domains/tesbakkie/disk.img,hda1,w',
            'file:/xen-images/domains/tesbakkie/swap.img,hda2,w' ]
name    = 'tesbakkie'
vif  = [ '' ]
on_poweroff = 'destroy'
on_reboot   = 'restart'
on_crash    = 'restart'
extra = "4"

---

### Post by aaahoopy on 2006-11-05
> **jgoor said:**
> Hi again!

After fiddling around I found that IMHO the howto of edgy lacks one thing: installation of bridge-utils.

What I did:
1) install bridge-utils
2) edit xend-config.sxp (replace 'dummy' with 'network-bridge')
3) restart xend
Now I got the xenbr0 and vif0.0 interfaces up.
After starting the DomU I immediately got an extra vif1.0 interface in Dom0 and I could ping the DomU.

*Now* I've got something *really* working!

Can someone please verify this?
Are these steps indeed missing from the howto by Jamie or am *I* missing something? Could it be done easier?

Config SNIPPED

I ran the script once, and when I noticed it was complaing about missing bridge-utils, I installed the package and reran the install script (no complaints on second run).  

I just looked at my config just now and verified that it is properly using bridging. YMMV.

John

---

