---
title: "compiling SARA, aka SATAN?"
date: 2006-01-04
forum: Desktop Environments
---

### Post by JustinHoMi on 2006-01-04
Hey. I'm trying to compile and install [SARA](http://www-arc.com/sara/) (previously known as SATAN). I'm just getting some errors while compiling that I haven't been able to remedy.

```
make[1]: Leaving directory `/home/ubuntu/Desktop/sara-6.0.7d/src/sssh'
make[1]: Entering directory `/home/ubuntu/Desktop/sara-6.0.7d'
cd src/rpcgen; make "LIBS=" "XFLAGS=-g -O  -I/usr/src/linux/include -I/home/ubuntu/Desktop/sara-6.0.7d/include/ansi  -Duid_t=int -Dgid_t=int -DGETGROUPS_T=int -DSYS_ERRLIST_DECLARED=1 -D_BSD_SOURCE=1 "
make[2]: Entering directory `/home/ubuntu/Desktop/sara-6.0.7d/src/rpcgen'
gcc -O -g -O  -I/usr/src/linux/include -I/home/ubuntu/Desktop/sara-6.0.7d/include/ansi  -Duid_t=int -Dgid_t=int -DGETGROUPS_T=int -DSYS_ERRLIST_DECLARED=1 -D_BSD_SOURCE=1    -c -o rpc_main.o rpc_main.c
In file included from /usr/include/stdlib.h:433,
                 from rpc_main.c:41:
/usr/include/sys/types.h:67: error: two or more data types in declaration specifiers
/usr/include/sys/types.h:82: error: two or more data types in declaration specifiers
make[2]: *** [rpc_main.o] Error 1
make[2]: Leaving directory `/home/ubuntu/Desktop/sara-6.0.7d/src/rpcgen'
make[1]: *** [rpcgen] Error 2
make[1]: Leaving directory `/home/ubuntu/Desktop/sara-6.0.7d'
make: *** [generic] Error 2
```

Any ideas? I can post additional information if necessary.

Thanks!
Justin

PS I'm using the VMWARE breezy image.

---

### Post by shortbus on 2007-12-05
This is what I get:

> slick@end-of-the-line:~/Desktop/sara-4.1.3a$ make
make[1]: Entering directory `/home/slick/Desktop/sara-4.1.3a'
cd src/misc; make "LIBS=-lnsl -lresolv -lrpcsvc" "XFLAGS=-g -O   -DGETGROUPS_T=gid_t -DSYS_ERRLIST_DECLARED=1 -D_BSD_SOURCE=1 " "RPCGEN=/usr/bin/rpcgen"
make[2]: Entering directory `/home/slick/Desktop/sara-4.1.3a/src/misc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/slick/Desktop/sara-4.1.3a/src/misc'
cd src/boot; make "LIBS=-lnsl -lresolv -lrpcsvc" "XFLAGS=-g -O   -DGETGROUPS_T=gid_t -DSYS_ERRLIST_DECLARED=1 -D_BSD_SOURCE=1 " "RPCGEN=/usr/bin/rpcgen"
make[2]: Entering directory `/home/slick/Desktop/sara-4.1.3a/src/boot'
make[2]: `../../bin/boot' is up to date.
make[2]: Leaving directory `/home/slick/Desktop/sara-4.1.3a/src/boot'
cd src/port_scan; make "LIBS=-lnsl -lresolv -lrpcsvc" "XFLAGS=-g -O   -DGETGROUPS_T=gid_t -DSYS_ERRLIST_DECLARED=1 -D_BSD_SOURCE=1 "
make[2]: Entering directory `/home/slick/Desktop/sara-4.1.3a/src/port_scan'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/slick/Desktop/sara-4.1.3a/src/port_scan'
cd src/nfs-chk; make "LIBS=-lnsl -lresolv -lrpcsvc" "XFLAGS=-g -O   -DGETGROUPS_T=gid_t -DSYS_ERRLIST_DECLARED=1 -D_BSD_SOURCE=1 " "RPCGEN=/usr/bin/rpcgen"
make[2]: Entering directory `/home/slick/Desktop/sara-4.1.3a/src/nfs-chk'
make[2]: `../../bin/nfs-chk' is up to date.
make[2]: Leaving directory `/home/slick/Desktop/sara-4.1.3a/src/nfs-chk'
cd src/yp-chk; make "LIBS=-lnsl -lresolv -lrpcsvc" "XFLAGS=-g -O   -DGETGROUPS_T=gid_t -DSYS_ERRLIST_DECLARED=1 -D_BSD_SOURCE=1 " "RPCGEN=/usr/bin/rpcgen"
make[2]: Entering directory `/home/slick/Desktop/sara-4.1.3a/src/yp-chk'
make[2]: `../../bin/yp-chk' is up to date.
make[2]: Leaving directory `/home/slick/Desktop/sara-4.1.3a/src/yp-chk'
cd src/fping; make "LIBS=-lnsl -lresolv -lrpcsvc" "CFLAGS=-g -O   -DGETGROUPS_T=gid_t -DSYS_ERRLIST_DECLARED=1 -D_BSD_SOURCE=1 "
make[2]: Entering directory `/home/slick/Desktop/sara-4.1.3a/src/fping'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/slick/Desktop/sara-4.1.3a/src/fping'
cd src/ddos_scan; make "LIBS=-lnsl -lresolv -lrpcsvc" "CFLAGS=-g -O   -DGETGROUPS_T=gid_t -DSYS_ERRLIST_DECLARED=1 -D_BSD_SOURCE=1 "
make[2]: Entering directory `/home/slick/Desktop/sara-4.1.3a/src/ddos_scan'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/slick/Desktop/sara-4.1.3a/src/ddos_scan'
cd src/contrib; make "LIBS=-lnsl -lresolv -lrpcsvc" "CFLAGS=-g -O   -DGETGROUPS_T=gid_t -DSYS_ERRLIST_DECLARED=1 -D_BSD_SOURCE=1 "
make[2]: Entering directory `/home/slick/Desktop/sara-4.1.3a/src/contrib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/slick/Desktop/sara-4.1.3a/src/contrib'
perl reconfig
checking to make sure all the target(s) are here...
Ok, trying to find perl5 now... hang on a bit...

Perl5 is in /usr/bin/perl5.8.8

changing the source in: bin/get_targets bin/faux_fping sara add_user bin/backdoor.sara bin/boot.sara bin/bounce.sara bin/cim.sara bin/depends.sara bin/dns-chk.sara bin/dns.sara bin/finger.sara bin/ftp.sara bin/hosttype.sara bin/http.sara bin/httpnew.sara bin/ie_mac.sara bin/imap.sara bin/login.sara bin/netstat.sara bin/nfs-chk.sara bin/pop3.sara bin/relay.sara bin/rex.sara bin/rexec.sara bin/rlogin.sara bin/rpc.sara bin/rsh.sara bin/rstatd.sara bin/rusers.sara bin/sendmail.sara bin/showmount.sara bin/smb.sara bin/snmpscan.sara bin/ssh.sara bin/systat.sara bin/tcpscan.sara bin/telnet.sara bin/tftp.sara bin/udpscan.sara bin/xhost.sara bin/yp-chk.sara bin/ypbind.sara bin/sample.sara.ext perl/html.pl perl/contrib/rfp_msadc.pl plugins/cis.pi bin/fwping

HTML/WWW Browser is /usr/bin/mozilla

So far so good...
Looking for all the commands now...

AEEEIIII...!!!  can't find mail


AEEEIIII...!!!  can't find tftp


AEEEIIII...!!!  can't find uudecode


AEEEIIII...!!!  can't find ypcat


AEEEIIII...!!!  can't find rusers


AEEEIIII...!!!  can't find showmount


AEEEIIII...!!!  can't find ypwhich


Ok, now doing substitutions on the shell scripts...
Changing paths in config/paths.pl...
Changing paths in config/paths.sh...

Now building CVE database

Now building FIFOs for SSS
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
SSS directory FIFOs will not be built, no Web Server found

make[1]: Leaving directory `/home/slick/Desktop/sara-4.1.3a'


---

### Post by jespdj on 2007-12-05
I have no idea what SARA is, but I hope this helps:

Make sure you install the programs mentioned: mail, tftp, uudecode, ypcat, rusers, showmount, ypwhich.
On [http://packages.ubuntu.com/](http://packages.ubuntu.com/) you should be able to lookup which Ubuntu packages contain those programs.

---

### Post by CaTeGoRe on 2008-03-25
Thanks,
Searching "package contains" on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) worked like a charm.
FYI: yp(yellow pages) is now in nis and uu is in sharutils

---

