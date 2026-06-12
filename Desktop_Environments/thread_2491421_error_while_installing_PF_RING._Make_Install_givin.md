---
title: "error while installing PF_RING. Make Install giving error"
date: 2023-10-08
forum: Desktop Environments
---

### Post by ahmex03 on 2023-10-08
I am trying to install PF_Ring on my Ubuntu by following steps on this guide [https://www.ntop.org/guides/pf_ring/thirdparty/snort-daq.html#compilation](https://www.ntop.org/guides/pf_ring/thirdparty/snort-daq.html#compilation) 

The problem is when I issue **$make install**, I am getting this error. 

> Libraries have been installed in:
   /usr/local/lib/daq

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the '-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the 'LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the 'LD_RUN_PATH' environment variable
     during linking
   - use the '-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to '/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[1]: Nothing to be done for 'install-data-am'.
make[1]: Leaving directory '/home/denes/Desktop/PF_RING/userland/snort/pfring-daq-module'

I tried many fixes like the one mentioned here [https://ehetherington.github.io/libtinylogger/guide/install-as-lib.html](https://ehetherington.github.io/libtinylogger/guide/install-as-lib.html) but no success. 
Can someone guide me what I am missing

---

### Post by ActionParsnip on 2023-10-10
You'll need to prefix "make install" with sudo as it is placing the binaries where they need to go in the file system. An ordinary user won't have access to do this

---

### Post by ActionParsnip on 2023-10-10
Or, just use this:
[https://packages.ntop.org/apt-stable/](https://packages.ntop.org/apt-stable/)

It has pfring-dkms
[https://packages.ntop.org/apt-stable/22.04/all/Packages](https://packages.ntop.org/apt-stable/22.04/all/Packages)

Much easier

---

### Post by ahmex03 on 2023-10-14
> **ActionParsnip said:**
> Or, just use this:
[https://packages.ntop.org/apt-stable/](https://packages.ntop.org/apt-stable/)

It has pfring-dkms
[https://packages.ntop.org/apt-stable/22.04/all/Packages](https://packages.ntop.org/apt-stable/22.04/all/Packages)

Much easier

I tried this [https://packages.ntop.org/apt-stable/](https://packages.ntop.org/apt-stable/)

When I issues last command,  [B]$ sudo apt install ./apt-ntop-stable.deb

[/B]I get this
> Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'apt-ntop-stable' instead of './apt-ntop-stable.deb'
apt-ntop-stable is already the newest version (2.9-25).
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

But when I try to get status of RF_Ring, its giving me this error. 

$** sudo systemctl status pf_ring.service**

> 
[COLOR=#ff0000]×[/COLOR] pf_ring.service - PF_RING service
     Loaded: loaded (/etc/systemd/system/pf_ring.service; enabled; vendor preset: enabled)
     Active: [COLOR=#ff0000]failed[/COLOR] (Result: exit-code) since Sat 2023-10-14 17:05:49 PKT; 6min ago
    Process: 59090 ExecStartPre=/bin/sh -c /bin/echo "$(/bin/date) pf_ring StartPre" >> /var/log/ntop-systemd.log (code=exited, status=0/SUCC>
    Process: 59093 ExecStartPre=/bin/sh -c if [ -x /etc/pf_ring/pre ]; then /etc/pf_ring/pre; fi (code=exited, status=0/SUCCESS)
    Process: 59094 ExecStart=/usr/bin/pf_ringctl start (code=exited, status=99)
    Process: 63698 ExecStopPost=/bin/sh -c /bin/echo "$(/bin/date) pf_ring StopPost" >> /var/log/ntop-systemd.log (code=exited, status=0/SUCC>
   Main PID: 59094 (code=exited, status=99)
        CPU: 18.960s

&#1575;&#1705;&#1578;&#1608;&#1576;&#1585; 14 17:05:47 denesPC pf_ringctl[63674]: is not newer than what is already found in kernel 6.2.0-34-generic (8.7.0).
&#1575;&#1705;&#1578;&#1608;&#1576;&#1585; 14 17:05:47 denesPC pf_ringctl[63674]: You may override by specifying --force.
&#1575;&#1705;&#1578;&#1608;&#1576;&#1585; 14 17:05:49 denesPC pf_ringctl[63691]: modprobe: ERROR: could not insert 'pf_ring': Invalid argument
&#1575;&#1705;&#1578;&#1608;&#1576;&#1585; 14 17:05:49 denesPC pf_ringctl[63693]: insmod: ERROR: could not insert module /lib/modules/6.2.0-34-generic/kernel/net/pf_ring/pf_ring>
&#1575;&#1705;&#1578;&#1608;&#1576;&#1585; 14 17:05:49 denesPC pf_ringctl[59094]:  * Unable to load PF_RING. Exiting
&#1575;&#1705;&#1578;&#1608;&#1576;&#1585; 14 17:05:49 denesPC pf_ringctl[59094]:    ...fail!
&#1575;&#1705;&#1578;&#1608;&#1576;&#1585; 14 17:05:49 denesPC systemd[1]: pf_ring.service: Main process exited, code=exited, status=99/n/a
&#1575;&#1705;&#1578;&#1608;&#1576;&#1585; 14 17:05:49 denesPC systemd[1]: pf_ring.service: Failed with result 'exit-code'.
&#1575;&#1705;&#1578;&#1608;&#1576;&#1585; 14 17:05:49 denesPC systemd[1]: [COLOR=#ff0000]Failed to start PF_RING service.[/COLOR]
&#1575;&#1705;&#1578;&#1608;&#1576;&#1585; 14 17:05:49 denesPC systemd[1]: pf_ring.service: Consumed 18.960s CPU time.

---

