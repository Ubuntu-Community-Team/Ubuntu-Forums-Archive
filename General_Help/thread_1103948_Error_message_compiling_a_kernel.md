---
title: "Error message compiling a kernel"
date: 2009-03-23
forum: General Help
---

### Post by angelsguitar on 2009-03-23
Hi. I'm running Interpid 64bit version, and I'm trying to compile a stock kernel but with the following options enabled/changed:

Processor type and features - Processor family - Core 2/Newer Xeon
Processor type and features - Preemption Model - Preemptible Kernel (Low Latency Desktop)
Processor type and features - Timer frequency (1000 HZ)

I'm currently using the linux-source package I downloaded with apt-get.  Basically I'm following the guide at [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile") compiling the "old fashioned" debian way.

When I try to compile the kernel, I get an error.  This is basically what I'm doing, and what I get:

```

angelsguitar@TSatellite:~/src/linux-source-2.6.27$ export CONCURRENCY_LEVEL=3
angelsguitar@TSatellite:~/src/linux-source-2.6.27$ fakeroot make-kpkg --initrd --append-to-version=-1khz kernel-image kernel-headers
exec make -f /usr/share/kernel-package/ruleset/minimal.mk debian APPEND_TO_VERSION=-1khz  INITRD=YES 
====== making target minimal_debian [new prereqs: ]======
This is kernel package version .
test -d debian || mkdir debian
test ! -e stamp-building || rm -f stamp-building
test -f debian/control || sed         -e 's/=V/2.6.27.10-1khz/g'        \
                -e 's/=D/2.6.27.10-1khz-10.00.Custom/g'         -e 's/=A/amd64/g'  \
	        -e 's/=SA//g'   -e 's/=L/ /g' \
                -e 's/=I//g'                                    \
                -e 's/=CV/2.6/g'                       \
                -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'                        \
                -e 's/=ST/linux/g'      -e 's/=B/xen/g'    \
		         /usr/share/kernel-package/Control > debian/control
test -f debian/changelog ||  sed -e 's/=V/2.6.27.10-1khz/g'             \
	    -e 's/=D/2.6.27.10-1khz-10.00.Custom/g'        -e 's/=A/amd64/g'       \
            -e 's/=ST/linux/g'     -e 's/=B/xen/g'         \
	    -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g' 	                    \
             /usr/share/kernel-package/changelog > debian/changelog
install -p -m 755 /usr/share/kernel-package/rules debian/rules
for file in ChangeLog  Control  Control.bin86 config templates.in rules; do                                      \
            cp -f  /usr/share/kernel-package/$file ./debian/;                               \
        done
for dir  in Config docs examples ruleset scripts pkg po;  do                                      \
          cp -af /usr/share/kernel-package/$dir  ./debian/;                                 \
        done
test -d ./debian/stamps || mkdir debian/stamps 
exec debian/rules  APPEND_TO_VERSION=-1khz  INITRD=YES  kernel-image kernel-headers 
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 3: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 4: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator

====== making target CONFIG-common [new prereqs: testdir]======

====== making target debian/stamp-conf [new prereqs: ]======
The changelog says we are creating 2.6.27.10-1khz.
However, I thought the version is ..-1khz
exit 3
make: *** [debian/stamp-conf] Error 3

```

What am I doing wrong, or leaving?

---

