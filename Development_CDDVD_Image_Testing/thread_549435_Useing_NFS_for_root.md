---
title: "Useing NFS for root"
date: 2007-09-12
forum: Development CD/DVD Image Testing
---

### Post by bexamous on 2007-09-12
My goal is to PXE boot loading the kernel/initrd and then use the livecd off a nfs server.

I am trying to follow this guide:
[http://thomas.enix.org/pub/livecd/HOWTO-Ubuntu-Live-Speedup](http://thomas.enix.org/pub/livecd/HOWTO-Ubuntu-Live-Speedup)

The problem I'm running into is getting dhclient to work in the initrd...  I can't get dhcp to compile... with or without the static patch..  

This is the error:
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o tr.o tr.c
tr.c:34: error: expected specifier-qualifier-list before ‘__u16’

I have to be doing something wrong.  This is in fiesty.

> root@UbuntuServer:~/mylive# apt-get source dhcp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Skipping already downloaded file 'dhcp_2.0pl5-19.5ubuntu2.dsc'
Skipping already downloaded file 'dhcp_2.0pl5.orig.tar.gz'
Skipping already downloaded file 'dhcp_2.0pl5-19.5ubuntu2.diff.gz'
Need to get 0B of source archives.
gpg: Signature made Thu 14 Dec 2006 02:35:05 AM PST using RSA key ID 2C0753E3
gpg: Can't check signature: public key not found
dpkg-source: extracting dhcp in dhcp-2.0pl5
dpkg-source: unpacking dhcp_2.0pl5.orig.tar.gz
dpkg-source: applying ./dhcp_2.0pl5-19.5ubuntu2.diff.gz
root@UbuntuServer:~/mylive# cd dhcp-2.0pl5/
root@UbuntuServer:~/mylive/dhcp-2.0pl5# ./configure
System Type: linux-2.2
root@UbuntuServer:~/mylive/dhcp-2.0pl5# make
Making all in common
make[1]: Entering directory `/root/mylive/dhcp-2.0pl5/common'
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o raw.o raw.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o parse.o parse.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o nit.o nit.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o icmp.o icmp.c
icmp.c: In function ‘icmp_echorequest’:
icmp.c:116: warning: cast from pointer to integer of different size
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o dispatch.o dispatch.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o conflex.o conflex.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o upf.o upf.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o bpf.o bpf.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o socket.o socket.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o lpf.o lpf.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o packet.o packet.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o memory.o memory.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o print.o print.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o options.o options.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o inet.o inet.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o convert.o convert.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o tree.o tree.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o tables.o tables.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o hash.o hash.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o alloc.o alloc.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o errwarn.o errwarn.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o inet_addr.o inet_addr.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o dlpi.o dlpi.c
cc -g  -I.. -I../includes -DLINUX_MAJOR=2 -DLINUX_MINOR=6   -c -o tr.o tr.c
tr.c:34: error: expected specifier-qualifier-list before ‘__u16’
tr.c: In function ‘insert_source_routing’:
tr.c:191: error: ‘struct routing_entry’ has no member named ‘rcf’
tr.c:192: error: ‘__u16’ undeclared (first use in this function)
tr.c:192: error: (Each undeclared identifier is reported only once
tr.c:192: error: for each function it appears in.)
tr.c:192: error: expected ‘;’ before ‘rcf’
tr.c:193: error: ‘struct routing_entry’ has no member named ‘rseg’
tr.c:194: error: ‘rcf’ undeclared (first use in this function)
tr.c:199: error: ‘struct routing_entry’ has no member named ‘access_time’
tr.c: In function ‘save_source_routing’:
tr.c:229: error: ‘__u16’ undeclared (first use in this function)
tr.c:229: error: expected ‘;’ before ‘rcf’
tr.c:246: error: ‘rcf’ undeclared (first use in this function)
tr.c:248: error: ‘struct routing_entry’ has no member named ‘rseg’
tr.c:248: error: ‘struct routing_entry’ has no member named ‘rseg’
tr.c:250: error: ‘struct routing_entry’ has no member named ‘rcf’
tr.c:251: error: ‘struct routing_entry’ has no member named ‘access_time’
tr.c:266: error: ‘struct routing_entry’ has no member named ‘access_time’
tr.c:271: error: ‘struct routing_entry’ has no member named ‘rseg’
tr.c:271: error: ‘struct routing_entry’ has no member named ‘rseg’
tr.c:273: error: ‘struct routing_entry’ has no member named ‘rcf’
tr.c: In function ‘expire_routes’:
tr.c:295: error: ‘struct routing_entry’ has no member named ‘access_time’
make[1]: *** [tr.o] Error 1
make[1]: Leaving directory `/root/mylive/dhcp-2.0pl5/common'
make: *** [all] Error 1
root@UbuntuServer:~/mylive/dhcp-2.0pl5# 






>  3) DHCP
 -------

Now, before mounting the NFS share, we need an IP and the simplest
solution is to get it through DHCP. The LiveCD scripts already uses
DHCP to get an IP, but they do it too late: after mounting the
CD-ROM. As in your case, we need to access the network before mouting
the fake CD-ROM, we'll do our own DHCP.

To do so, we will compile a static binary of dhclient. We must do that
because the dynamic version of dhclient (compiled out of the initrd,
and then copied inside the initrd) doesn't work:
# dhclient
 ...
dhclient: relocation error: dhclient: symbol htons, version GLIBC_2.0
not defined in file libc.so.6 with link time reference

So, let's go for a static dhclient:
 $ apt-get source dhcp
 $ cd dhcp-2.0pl5

Fetch the patch that modifies the compilation process of dhcp-client
to generate a static binary, and apply it:
 $ wget [http://thomas.enix.org/pub/livecd/dhcp-static.patch](http://thomas.enix.org/pub/livecd/dhcp-static.patch)
 $ patch -p1 < dhcp-static.patch

Also apply a needed Debian patch:
 $ patch -p1 < debian/patches/200_script.patch

Configure, and compile:
 $ ./configure
 $ make

The static binary is client/dhclient.static. Let's copy it inside the
initrd, copy the dhclient script, and create the directory where
dhclient stores its leases files:
 $ sudo cp client/dhclient.static ../initrd.dir/sbin/dhclient
 $ sudo cp client/scripts/linux ../initrd.dir/etc/dhclient-script
 $ sudo mkdir -p ../initrd.dir/var/state/dhcp/
 $ cd ../

Create a dhclient.conf in the initrd:
 $ sudo vi initrd.dir/etc/dhclient.conf

And add the following line to it:

-------------------------->8---------------------------
request option-128, option-129;
-------------------------->8---------------------------


---

### Post by bexamous on 2007-10-26
Okay I ended up getting everything to work how I needed...  solution?  Use 7.04 where NFS is already setup.


On the PXE server I use this which will basically work...
LABEL nfs
        kernel nfs/vmlinuz
        append initrd=nfs/newinitrd.gz root=/dev/nfs rw  nfsroot=192.168.3.1:/work/chroot ip=dhcp --

The NFS server is sharing the compressed file system off the CD... everything else is easy to setup.

If you do nothing else it'll boot to your live CD except its writable and you can destroy the filesystem...  you also cannot have lots of systems using this same NFS image.... SOO

You have to edit the initrd iamge on the PXE server and in one of the scripts/nfs* files you have to setup the unionfs with a ramdrive.  Then it will act just like a livecd, everyone can share the NFS image (set to ro), YAY.

This is basically what the scripts/nfs file does now:
nfsmount -o nolock ${roflag} ${NFSOPTS} ${NFSROOT} ${rootmnt}
mount -n -t tmpfs tmpfs /cow
mount -n -t unionfs -o dirs=/cow=rw:${rootmnt}=nfsro unionfs "${rootmnt}"

---

