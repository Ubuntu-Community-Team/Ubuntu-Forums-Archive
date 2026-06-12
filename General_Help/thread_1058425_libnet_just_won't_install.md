---
title: "libnet just won't install"
date: 2009-02-02
forum: General Help
---

### Post by v1nsai on 2009-02-02
I've been trying to install libnet in order to compile a different package.  I've downloaded it from 2 different sources and gotten the same results when I try to compile.  Here's the commands I used and their results:

'./configure' (seems to work)

```
beginning autoconfiguration process for libnet-1.1.2.1...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking machine endianess... lil
checking if unaligned accesses fail... no
checking whether gcc needs -traditional... no
checking for strerror... yes
checking link-layer packet interface type... found linux primitives
checking for packet socket (PF_SOCKET)... test program got EPERM... assuming yes
checking for Linux proc filesystem... yes
scanning available packet construction modules: 802.1q 802.1x 802.2 802.3 arp bgp cdp data dhcp dns ethernet fddi gre icmp igmp ip ipsec isl link mpls ntp ospf rip rpc sebek snmp stp tcp token_ring udp vrrp 
checking net/ethernet.h usability... yes
checking net/ethernet.h presence... yes
checking for net/ethernet.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating include/Makefile
config.status: creating include/libnet/Makefile
config.status: creating sample/Makefile
config.status: creating version.h
config.status: creating include/libnet.h
config.status: creating libnet-config
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: executing depfiles commands
config.status: executing default commands

```

'make'

```
Making all in include
make[1]: Entering directory `/home/v1nsai/Desktop/libnet/include'
make  all-recursive
make[2]: Entering directory `/home/v1nsai/Desktop/libnet/include'
Making all in libnet
make[3]: Entering directory `/home/v1nsai/Desktop/libnet/include/libnet'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/v1nsai/Desktop/libnet/include/libnet'
make[3]: Entering directory `/home/v1nsai/Desktop/libnet/include'
make[3]: Leaving directory `/home/v1nsai/Desktop/libnet/include'
make[2]: Leaving directory `/home/v1nsai/Desktop/libnet/include'
make[1]: Leaving directory `/home/v1nsai/Desktop/libnet/include'
Making all in src
make[1]: Entering directory `/home/v1nsai/Desktop/libnet/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/v1nsai/Desktop/libnet/src'
Making all in sample
make[1]: Entering directory `/home/v1nsai/Desktop/libnet/sample'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/v1nsai/Desktop/libnet/sample'
make[1]: Entering directory `/home/v1nsai/Desktop/libnet'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/v1nsai/Desktop/libnet'

```

'make install'

```
Making install in include
make[1]: Entering directory `/home/v1nsai/Desktop/libnet/include'
Making install in libnet
make[2]: Entering directory `/home/v1nsai/Desktop/libnet/include/libnet'
make[3]: Entering directory `/home/v1nsai/Desktop/libnet/include/libnet'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../mkinstalldirs /usr/include/libnet
 /usr/bin/install -c -m 644 libnet-asn1.h /usr/include/libnet/libnet-asn1.h
/usr/bin/install: cannot remove `/usr/include/libnet/libnet-asn1.h': Permission denied
 /usr/bin/install -c -m 644 libnet-functions.h /usr/include/libnet/libnet-functions.h
/usr/bin/install: cannot remove `/usr/include/libnet/libnet-functions.h': Permission denied
 /usr/bin/install -c -m 644 libnet-headers.h /usr/include/libnet/libnet-headers.h
/usr/bin/install: cannot remove `/usr/include/libnet/libnet-headers.h': Permission denied
 /usr/bin/install -c -m 644 libnet-macros.h /usr/include/libnet/libnet-macros.h
/usr/bin/install: cannot remove `/usr/include/libnet/libnet-macros.h': Permission denied
 /usr/bin/install -c -m 644 libnet-structures.h /usr/include/libnet/libnet-structures.h
/usr/bin/install: cannot remove `/usr/include/libnet/libnet-structures.h': Permission denied
 /usr/bin/install -c -m 644 libnet-types.h /usr/include/libnet/libnet-types.h
/usr/bin/install: cannot remove `/usr/include/libnet/libnet-types.h': Permission denied
make[3]: *** [install-libnetincludeHEADERS] Error 1
make[3]: Leaving directory `/home/v1nsai/Desktop/libnet/include/libnet'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/v1nsai/Desktop/libnet/include/libnet'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/v1nsai/Desktop/libnet/include'
make: *** [install-recursive] Error 1
```

---

### Post by Yellow Pasque on 2009-02-02
```
sudo make install
```

---

### Post by v1nsai on 2009-02-02
Hehe, I've gotten caught in the 'sudo' trap before but I tried that too.  The results of a 'sudo make install' are different from a normal 'make install' however, so I'll go ahead and post those too.

```
Making install in include
make[1]: Entering directory `/home/v1nsai/Desktop/libnet/include'
Making install in libnet
make[2]: Entering directory `/home/v1nsai/Desktop/libnet/include/libnet'
make[3]: Entering directory `/home/v1nsai/Desktop/libnet/include/libnet'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../mkinstalldirs /usr/include/libnet
 /usr/bin/install -c -m 644 libnet-asn1.h /usr/include/libnet/libnet-asn1.h
 /usr/bin/install -c -m 644 libnet-functions.h /usr/include/libnet/libnet-functions.h
 /usr/bin/install -c -m 644 libnet-headers.h /usr/include/libnet/libnet-headers.h
 /usr/bin/install -c -m 644 libnet-macros.h /usr/include/libnet/libnet-macros.h
 /usr/bin/install -c -m 644 libnet-structures.h /usr/include/libnet/libnet-structures.h
 /usr/bin/install -c -m 644 libnet-types.h /usr/include/libnet/libnet-types.h
make[3]: Leaving directory `/home/v1nsai/Desktop/libnet/include/libnet'
make[2]: Leaving directory `/home/v1nsai/Desktop/libnet/include/libnet'
make[2]: Entering directory `/home/v1nsai/Desktop/libnet/include'
make[3]: Entering directory `/home/v1nsai/Desktop/libnet/include'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/include
 /usr/bin/install -c -m 644 libnet.h /usr/include/libnet.h
make[3]: Leaving directory `/home/v1nsai/Desktop/libnet/include'
make[2]: Leaving directory `/home/v1nsai/Desktop/libnet/include'
make[1]: Leaving directory `/home/v1nsai/Desktop/libnet/include'
Making install in src
make[1]: Entering directory `/home/v1nsai/Desktop/libnet/src'
make[2]: Entering directory `/home/v1nsai/Desktop/libnet/src'
/bin/bash ../mkinstalldirs /usr/lib
 /usr/bin/install -c -m 644 libnet.a /usr/lib/libnet.a
 ranlib /usr/lib/libnet.a
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/v1nsai/Desktop/libnet/src'
make[1]: Leaving directory `/home/v1nsai/Desktop/libnet/src'
Making install in sample
make[1]: Entering directory `/home/v1nsai/Desktop/libnet/sample'
make[2]: Entering directory `/home/v1nsai/Desktop/libnet/sample'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/v1nsai/Desktop/libnet/sample'
make[1]: Leaving directory `/home/v1nsai/Desktop/libnet/sample'
make[1]: Entering directory `/home/v1nsai/Desktop/libnet'
make[2]: Entering directory `/home/v1nsai/Desktop/libnet'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/v1nsai/Desktop/libnet'
make[1]: Leaving directory `/home/v1nsai/Desktop/libnet'

```

---

