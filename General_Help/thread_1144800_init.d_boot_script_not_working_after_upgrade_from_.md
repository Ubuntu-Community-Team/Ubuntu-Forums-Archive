---
title: "init.d boot script not working after upgrade from 8.10 to 9.04"
date: 2009-05-01
forum: General Help
---

### Post by usingruby on 2009-05-01
After upgrading from ubuntu 8.10 to 9.04 a custom init.d script stopped to work. The script is perfectly working from a console if I login, but does not work in the startup process. I am not sure where I can find the correct logs to identify the error.

The boot script is attached. The user is my ubuntu user account. For me it looks like an authorization/access problem, because the script works after I have logged in.

* I added the script to the boot process via BUM and readded it after the upgrade to 9.04
* I tried to add this script to an other working boot up script (SqueezeCenter) the SqueezeCenter server is started so I am sure that the script is executed but the MusicIP service did not start up

Did something change in the start up process that needs to be taken care of?

I found this in a log:
Apr 29 07:50:19 erde su[13678]: Successful su for klaas by root
Apr 29 07:50:20 erde su[13678]: + ??? root:klaas
Apr 29 07:50:22 erde su[13678]: pam_unix(su:session): session opened for user klaas by (uid=0)
Apr 29 07:50:23 erde dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.34" (uid=1000 pid=6551 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.68" (uid=0 pid=13678 comm="su - klaas -c /usr/local/mmserver/MusicMagicServer"))
Apr 29 07:50:23 erde su[13678]: pam_unix(su:session): session closed for user klaas

Regards Klaas

---

### Post by usingruby on 2009-05-03
anyone has a tip where to look or what to read, to find out more? I would need a starting point to get this issue fixed.

Thank you very much
Klaas

---

### Post by MaxIBoy on 2009-05-03
I think Jaunty has put the login part sooner in the boot process. Try moving your custom script before gdm.

---

### Post by usingruby on 2009-05-04
this did not help, I moved it directly prior gdm, but I get the same messages in the "auth.log" I am wondering if this is the real error because the auth.log has many errors like this listed only for other commands.

---

### Post by pico on 2009-05-05
I have the sema scenario and the same problem. On 2 different PC.

Some custom services (nagios and dekiwiki in my case) do not start in automatic after reboot.
Since Ubuntu 8.04 I nave no problem with this services, but 9.04 seems to ignore the service and do not start it.

I have also no idea on direction to investigate....

---

### Post by usingruby on 2009-05-06
I don't know what happened, the new updates solved it for me! No errors in the auth.log, so it must be some changes from yesterdays updates :) Hopefully it stays this way!

---

### Post by pico on 2009-05-07
No WAY for ME!

Today Update do not solve the problem!

On one of 2 PC where I have problem (here I have installed nagios) I have this absurd situation:

```
pico@ubuntusrv1:~$ sudo /etc/init.d/nagios checkconfig
Running configuration check... OK.
pico@ubuntusrv1:~$ sudo /etc/init.d/nagios status
nagios is not running
pico@ubuntusrv1:~$ sudo /etc/init.d/nagios start
Starting nagios: done.
pico@ubuntusrv1:~$ sudo /etc/init.d/nagios status
nagios is not running
pico@ubuntusrv1:~$ ps -ef |grep nagios
pico      5113  4901  0 11:56 pts/0    00:00:00 grep nagios
pico@ubuntusrv1:~$
```

Logs give no help!
Can somebody help me please ??
ciao

---

### Post by usingruby on 2009-05-07
okay, removed the SOLVED status. Maybe you should fill a bug report with launchpad?

---

### Post by digitalsushi on 2009-05-07
We have a similar issue.  On Ubuntu 9.04 and Kubuntu 9.04, we have an init.d script called from runlevel 2 for auto-start.  We noticed that it doesn't run after the system is loaded.  We replaced our service with a script that does nothing but report when signals are received.  We learned that something (probably the parent process) sends a SIGHUP and then a SIGTERM to our program.  We're not sure what it is.  A workaround solution is to prefix your service with a "nohup" command (inside your init.d script, not of the script itself).  If you're unfamiliar with nohup, it simply intercepts any SIGHUP signals sent by a parent and shields them from reaching your program.  In our case, it allows our service to work in Ubuntu 9.04.

If anyone knows why the service is being sent these signals, we'd love to learn more.  Thanks.

---

### Post by usingruby on 2009-05-07
I have no idea, it worked once (as posted before), then it stopped working again with no additional updates :( So the bug is still there and I have no idea why it was starting once. A different user reported the same on a different forum.

So maybe we should fill a bug report with nearly no information.

---

### Post by pico on 2009-05-08
I have yust posted a bug:
[https://bugs.launchpad.net/ubuntu/+bug/372633](https://bugs.launchpad.net/ubuntu/+bug/372633)

But nobody still answer.

Very very strange behaviour!

---

### Post by usingruby on 2009-05-08
> **digitalsushi said:**
> A workaround solution is to prefix your service with a "nohup" command (inside your init.d script, not of the script itself).  

Thank you very much, the nohup workaround saved my day. At least I can start the service till the bug is resolved!

---

### Post by pico on 2009-05-08
Can you explain more in details how to proceed with this workaoround?

Inside the folder /etc/init.d there are a lot of script.
Where I have to put the "nohup" command ?

In the first line of the service that do not start in auto? or where ??

regards

---

### Post by windracer01 on 2009-05-08
I'm having the same exact problem after upgrading from 8.10 to 9.04. All my custom services start just fine *except* Nagios 3.1.0. I tried the nohup trick in the init script but that didn't help either.

If I run nagios straight from the command-line, without daemonizing (the -d switch), I get this:

```
Nagios 3.1.0
Copyright (c) 1999-2009 Ethan Galstad (http://www.nagios.org)
Last Modified: 01-25-2009
License: GPL

Nagios 3.1.0 starting... (PID=3078)
Local time is Fri May 08 21:03:36 EDT 2009
*** stack smashing detected ***: ./nagios terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7e98da8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7e98d60]
./nagios[0x8083ba2]
./nagios(check_for_nagios_updates+0x6a)[0x8083c1a]
./nagios(main+0x552)[0x8058cc2]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7db1775]
./nagios[0x80586d1]
======= Memory map: ========
08048000-080d7000 r-xp 00000000 08:01 8308982    /usr/local/nagios/bin/nagios
080d7000-080d8000 r--p 0008e000 08:01 8308982    /usr/local/nagios/bin/nagios
080d8000-080d9000 rw-p 0008f000 08:01 8308982    /usr/local/nagios/bin/nagios
080d9000-080da000 rw-p 080d9000 00:00 0
09dd4000-09df5000 rw-p 09dd4000 00:00 0          [heap]
b752d000-b753a000 r-xp 00000000 08:01 4620341    /lib/libgcc_s.so.1
b753a000-b753b000 r--p 0000c000 08:01 4620341    /lib/libgcc_s.so.1
b753b000-b753c000 rw-p 0000d000 08:01 4620341    /lib/libgcc_s.so.1
b753c000-b754e000 r-xp 00000000 08:01 4621550    /lib/tls/i686/cmov/libresolv-2.9.so
b754e000-b754f000 r--p 00011000 08:01 4621550    /lib/tls/i686/cmov/libresolv-2.9.so
b754f000-b7550000 rw-p 00012000 08:01 4621550    /lib/tls/i686/cmov/libresolv-2.9.so
b7550000-b7552000 rw-p b7550000 00:00 0
b7552000-b7553000 ---p b7552000 00:00 0
b7553000-b7d53000 rw-p b7553000 00:00 0
b7d53000-b7d5d000 r-xp 00000000 08:01 4620537    /lib/tls/i686/cmov/libnss_files-2.9.so
b7d5d000-b7d5e000 r--p 00009000 08:01 4620537    /lib/tls/i686/cmov/libnss_files-2.9.so
b7d5e000-b7d5f000 rw-p 0000a000 08:01 4620537    /lib/tls/i686/cmov/libnss_files-2.9.so
b7d5f000-b7d68000 r-xp 00000000 08:01 4621542    /lib/tls/i686/cmov/libnss_nis-2.9.so
b7d68000-b7d69000 r--p 00008000 08:01 4621542    /lib/tls/i686/cmov/libnss_nis-2.9.so
b7d69000-b7d6a000 rw-p 00009000 08:01 4621542    /lib/tls/i686/cmov/libnss_nis-2.9.so
b7d6a000-b7d7f000 r-xp 00000000 08:01 4620480    /lib/tls/i686/cmov/libnsl-2.9.so
b7d7f000-b7d80000 r--p 00014000 08:01 4620480    /lib/tls/i686/cmov/libnsl-2.9.so
b7d80000-b7d81000 rw-p 00015000 08:01 4620480    /lib/tls/i686/cmov/libnsl-2.9.so
b7d81000-b7d83000 rw-p b7d81000 00:00 0
b7d83000-b7d8a000 r-xp 00000000 08:01 4620513    /lib/tls/i686/cmov/libnss_compat-2.9.so
b7d8a000-b7d8b000 r--p 00006000 08:01 4620513    /lib/tls/i686/cmov/libnss_compat-2.9.so
b7d8b000-b7d8c000 rw-p 00007000 08:01 4620513    /lib/tls/i686/cmov/libnss_compat-2.9.so
b7d96000-b7d97000 rw-p b7d96000 00:00 0
b7d97000-b7d99000 r-xp 00000000 08:01 4620461    /lib/tls/i686/cmov/libdl-2.9.so
b7d99000-b7d9a000 r--p 00001000 08:01 4620461    /lib/tls/i686/cmov/libdl-2.9.so
b7d9a000-b7d9b000 rw-p 00002000 08:01 4620461    /lib/tls/i686/cmov/libdl-2.9.so
b7d9b000-b7ef7000 r-xp 00000000 08:01 4620450    /lib/tls/i686/cmov/libc-2.9.so
b7ef7000-b7ef8000 ---p 0015c000 08:01 4620450    /lib/tls/i686/cmov/libc-2.9.so
b7ef8000-b7efa000 r--p 0015c000 08:01 4620450    /lib/tls/i686/cmov/libc-2.9.so
b7efa000-b7efb000 rw-p 0015e000 08:01 4620450    /lib/tls/i686/cmov/libc-2.9.so
b7efb000-b7efe000 rw-p b7efb000 00:00 0
b7efe000-b7f05000 r-xp 00000000 08:01 7962657    /usr/lib/libltdl.so.7.2.0
b7f05000-b7f06000 r--p 00006000 08:01 7962657    /usr/lib/libltdl.so.7.2.0
b7f06000-b7f07000 rw-p 00007000 08:01 7962657    /usr/lib/libltdl.so.7.2.0
b7f07000-b7f08000 rw-p b7f07000 00:00 0
b7f08000-b7f1d000 r-xp 00000000 08:01 4621548    /lib/tls/i686/cmov/libpthread-2.9.so
b7f1d000-b7f1e000 r--p 00014000 08:01 4621548    /lib/tls/i686/cmov/libpthread-2.9.so
b7f1e000-b7f1f000 rw-p 00015000 08:01 4621548    /lib/tls/i686/cmov/libpthread-2.9.so
b7f1f000-b7f21000 rw-p b7f1f000 00:00 0
b7f21000-b7f45000 r-xp 00000000 08:01 4620467    /lib/tls/i686/cmov/libm-2.9.so
b7f45000-b7f46000 r--p 00023000 08:01 4620467    /lib/tls/i686/cmov/libm-2.9.so
b7f46000-b7f47000 rw-p 00024000 08:01 4620467    /lib/tls/i686/cmov/libm-2.9.so
b7f49000-b7f4e000 r-xp 00000000 08:01 4620529    /lib/tls/i686/cmov/libnss_dns-2.9.so
b7f4e000-b7f4f000 r--p 00004000 08:01 4620529    /lib/tls/i686/cmov/libnss_dns-2.9.so
b7f4f000-b7f50000 rw-p 00005000 08:01 4620529    /lib/tls/i686/cmov/libnss_dns-2.9.so
b7f50000-b7f53000 rw-p b7f50000 00:00 0
b7f53000-b7f54000 r-xp b7f53000 00:00 0          [vdso]
b7f54000-b7f70000 r-xp 00000000 08:01 4620368    /lib/ld-2.9.so
b7f70000-b7f71000 r--p 0001b000 08:01 4620368    /lib/ld-2.9.so
b7f71000-b7f72000 rw-p 0001c000 08:01 4620368    /lib/ld-2.9.so
bfa5c000-bfa71000 rw-p bffeb000 00:00 0          [stack]
Aborted

```Does "stack smashing" mean anything to anyone? I've added this to the bug report.

---

### Post by dcstar on 2009-05-08
Just out of interest, there is a Launchpad bug where the Gnome Root terminal no long runs in 9.04:

[https://bugs.launchpad.net/bugs/328575](https://bugs.launchpad.net/bugs/328575)

I wonder if there is a relationship with other root-level processes not working?

---

### Post by pico on 2009-05-09
Can you post the exact command you run ?
I have tried:

```
pico@ubuntusrv1:~$ sudo /etc/init.d/nagios -d restart
[sudo] password for pico:
Usage: nagios {start|stop|restart|reload|force-reload|status|checkconfig}
pico@ubuntusrv1:~$
```

but it does not work !
THX

---

### Post by usingruby on 2009-05-09
> **pico said:**
> 
Inside the folder /etc/init.d there are a lot of script.
Where I have to put the "nohup" command ?


You have to edit the script that is not working. Example for me:
/etc/init.d/mmserver

using my favourite editor changing the script from:
```
USER="klaas"
# PATH TO THE MUSICMAGICMIXERSERVER 
export MUSICHOME="/usr/local/mmserver/"
case $1 in
    start)
	su - $USER -c $MUSICHOME"MusicMagicServer start  & > /dev/null" 
	echo "Running MusicMagicServer"
	exit
	;;
    stop)
	su - $USER -c $MUSICHOME"MusicMagicServer stop  & > /dev/null" 
	echo "Stopped MusicMagicServer"
	exit
	;;
    *)
        echo "Usage: /etc/rc.d/init.d/mmserver { start | stop }"
	exit
	;;
esac
```

to:
```
USER="klaas"
# PATH TO THE MUSICMAGICMIXERSERVER 
export MUSICHOME="/usr/local/mmserver/"
case $1 in
    start)
	nohup su - $USER -c $MUSICHOME"MusicMagicServer start  & > /dev/null" 
	echo "Running MusicMagicServer"
	exit
	;;
    stop)
	nohup su - $USER -c $MUSICHOME"MusicMagicServer stop  & > /dev/null" 
	echo "Stopped MusicMagicServer"
	exit
	;;
    *)
        echo "Usage: /etc/rc.d/init.d/mmserver { start | stop }"
	exit
	;;
esac
```

so I changed the call to start my daemon by prefixing the line with nohup ```

su - $USER -c $MUSICHOME"MusicMagicServer start
nohup su - $USER -c $MUSICHOME"MusicMagicServer start
```

You must do the same for your scripts.

---

### Post by Alterax on 2009-05-09
It's also worth mentioning that with Jaunty, init scripts have given way to upstart scripts during the boot process.  You can still call init scripts from the shell, but if you want them to start at boot, your script must either be called or started from upstart.

The devs made this switch because upstart can handle multiple scripts simultaneously rather than in a serial manner, which in turn speeds up boot time.

I haven't an Ubuntu installation handy myself, or I would walk you through the process.  But dig around in /etc/upstart.d/ and I'm sure you can figure out what changes must be made to get your script working.

---

### Post by pico on 2009-05-09
I'm also affected of this other bug:
[https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/328575](https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/328575)

Anybody else ??

---

### Post by pico on 2009-05-11
The "nohup" trick do not work for me !

In addiction, if I run nagios without "-d" option I receive :

```
*** stack smashing detected ***: ./nagios terminated
```

---

### Post by windracer01 on 2009-05-11
> **pico said:**
> The nohup trick do not work for me !

In addiction, if I run nagios without &quot;-d&quot; option I receive :

```
*** stack smashing detected ***: ./nagios terminated
```
You and I are in the exact same boat. I've given up on running Nagios for now until someone else can figure this out for us ...

---

### Post by pico on 2009-05-11
I'm curious to install ubuntu from scrartch and then nagios again on a new machine to find out if it work!
But now I have no time...

---

### Post by pico on 2009-05-13
I have Installed from scratch a new Ubuntu 9.04.. and then installed Nagios 3.0.6 from synaptic packages (not from source!!).

It works with no problem.
So I'm quite sure this problem is related to the upgrade process. But I have no idea on how to solve it.

Regards

---

### Post by windracer01 on 2009-05-19
No new news on this, eh? I'm really missing having Nagios monitoring my network and I cannot for the life of me get it to run on 9.04 after upgrading. I'll try re-compiling from source, but I'm not enthusiastic that will solve the problem.

*edit:* uh, wow, ok. I downloaded the stable 3.06 Nagios branch and compiled it on my 9.04 (upgraded box) and it's working now! I guess next I'll try re-compiling 3.1.0 and see if that will work again.

---

### Post by preachermanx on 2009-06-05
> **windracer01 said:**
> No new news on this, eh? I'm really missing having Nagios monitoring my network and I cannot for the life of me get it to run on 9.04 after upgrading. I'll try re-compiling from source, but I'm not enthusiastic that will solve the problem.

*edit:* uh, wow, ok. I downloaded the stable 3.06 Nagios branch and compiled it on my 9.04 (upgraded box) and it's working now! I guess next I'll try re-compiling 3.1.0 and see if that will work again.


Any success with this? I am running into the same problem on a fresh 9.04 build and the latest 3.1.0 release.

---

### Post by windracer01 on 2009-06-06
> **preachermanx said:**
> Any success with this? I am running into the same problem on a fresh 9.04 build and the latest 3.1.0 release.
I didn't try. Since I've got 3.0.6 working again I just decided to stick with it for now.

---

### Post by windracer01 on 2009-06-22
I'm going to try this tomorrow, but Nagios 3.1.1 was released today and I saw this in the release notes:

> * Fix for failure to daemonize - Nagios now bails (bug #0000011)

Related?

---

### Post by windracer01 on 2009-06-23
It seems to have worked! I've got Nagios 3.1.1 running under 9.04 (via the init script).

---

