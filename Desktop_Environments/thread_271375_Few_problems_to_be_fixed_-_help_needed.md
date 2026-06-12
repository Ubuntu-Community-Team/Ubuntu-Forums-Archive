---
title: "Few problems to be fixed - help needed"
date: 2006-10-04
forum: Desktop Environments
---

### Post by qsz on 2006-10-04
I installed the latest Ubuntu about a month ago and I like it more and more every day. But I have few problems which have been bothering me since the beginning.

1. Printer drivers. My printer is Canon i250 and I downloaded the driver called Bjfilter from Canon's site. I did everything like the INSTALL-file told to do. ./autogen.sh went fine, compiling the package caused problems:

> Now type `make' to compile the package.
root@qsz:/home/miika/bjfilter-2.3-0# make
make  all-recursive
make[1]: Siirrytään hakemistoon "/home/miika/bjfilter-2.3-0"
Making all in src
make[2]: Siirrytään hakemistoon "/home/miika/bjfilter-2.3-0/src"
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include/cncl -I../include/misc    -O2 -MT bjferror.o -MD -MP -MF ".deps/bjferror.Tpo" -c -o bjferror.o bjferror.c; \
        then mv -f ".deps/bjferror.Tpo" ".deps/bjferror.Po"; else rm -f ".deps/bjferror.Tpo"; exit 1; fi
bjferror.c: In function ‘bjf_error’:
bjferror.c:49: error: label at end of compound statement
make[2]: *** [bjferror.o] Virhe 1
make[2]: Poistutaan hakemistosta "/home/miika/bjfilter-2.3-0/src"
make[1]: *** [all-recursive] Virhe 1
make[1]: Poistutaan hakemistosta "/home/miika/bjfilter-2.3-0"
make: *** [all] Virhe 2
root@qsz:/home/miika/bjfilter-2.3-0#

My Ubuntu is Finnish version, poistutaan hakemistosta=exiting directory, Virhe=error. I've tried to google for help but I have absolutely no idea what to do.

2. Making Firestarter to start up at login. I've added *sudo firestarter --start-hidden* to the Startup programs and added *miika ALL= NOPASSWD: /usr/bin/firestarter* to the */etc/sudoers* (to prevent Ubuntu from asking the password). The problem is nothing happens. It though shows up in running programs but something is wrong.
[IMG]http://koti.mbnet.fi/qsz/kuvat/snapshot1.png[/IMG]
Any ideas?

3. Installing Compiz. I have working NVIDIA drivers so the problem isn't that. I have looked help from the [Ubuntu how to](http://ubuntuguide.org/wiki/Ubuntu_dapper_fi#How_to_install_Xgl.2FCompiz_.28Nvidia.29) but the error comes when executing *sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome*. It says that some packets could not have be installed and compiz has dependency on compiz-plugins (>= 0.2) but it's not marked to be installed. Trying to install compiz-plugins causes error which says it has dependency on compiz-core and csm. And compiz-core is already installed and the latest version. :-k 

I hope somebody did understand.

4. Azureus bittorrent client. Every time I start Azureus I get an error message window to the bottom right corner of my screen. It says that Azureus was shutdown incorrectly (which isn't true). The message box can't be closed, even xkill won't help. I read that it's something with java, I'm using Sun. Obviously it's a bug, how to get rid of it?


I really hope someone could help me with these issues. Thanks already.

---

### Post by Delkster on 2006-10-04
> **qsz said:**
> 1. Printer drivers. My printer is Canon i250 and I downloaded the driver called Bjfilter from Canon's site. I did everything like the INSTALL-file told to do. ./autogen.sh went fine, compiling the package caused problems:

I found a couple of threads that might be of interest:
[http://www.ubuntuforums.org/showthread.php?t=80528](http://www.ubuntuforums.org/showthread.php?t=80528)
[http://www.ubuntuforums.org/showthread.php?t=126063](http://www.ubuntuforums.org/showthread.php?t=126063)

They seem to be quite old and about the Breezy Badger release (5.10) rather than the latest one but maybe you could still find some pointers there. I've probably never even seen that kind of a printer so other than that, it's hard to help.

AFAIK "label at end of compound statement" refers to certain kind of bad syntax that has been accepted by the compiler in the past but is nowadays at least deprecated if not completely unsupported.

> 2. Making Firestarter to start up at login.
You shouldn't really need to have Firestarter launched on login. It's really just a GUI for easy configuration of firewalling rules, and the actual filtering is done by the Linux kernel. The filtering is done even if the Firestarter GUI isn't running continuously.

Firestarter adds a startup script that sets the filtering rules according to your configuration at system boot, so you don't have to run the GUI every time you start your computer. Maybe you should check that you have "Firestarter > Edit > Preferences > Firewall > Start/restart firewall on DHCP lease renewal" selected, though (assuming that you're using a broadband connection, not dial-up).

That said, for some reason the init script (to be run at system boot) created by Firestarter seems to fail for me so it doesn't actually set any rules, thus effectively leaving the firewall disabled. Issuing "sudo /etc/init.d/firestarter restart" later seems to work, though. I can't investigate the matter more now but it might be interesting to hear if you experience the same. You can check whether you have any firewalling enabled by commanding "sudo iptables -L", which lists all filtering rules given to the kernel. If it produces something like this, there are no rules:
```

$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

If the command produces longer and more diverse output, there are at least some rules and the init script has probably done its job.

> 3. Installing Compiz.
I'll skip this part at least for now, as I don't have much experience with compiz (I've tried it once), and I'm still running the stable Dapper Drake release and will probably wait for Edgy Eft to be released before I try AIGLX/compositing again.


> 4. Azureus bittorrent client. Every time I start Azureus I get an error message window to the bottom right corner of my screen. It says that Azureus was shutdown incorrectly (which isn't true). The message box can't be closed, even xkill won't help. I read that it's something with java, I'm using Sun. Obviously it's a bug, how to get rid of it?
The Azureus package in Ubuntu doesn't seem to work very well. I've just manually installed Azureus from the original upstream package, and it works okay (apart from the GUI showing some glitches, and not considering that it's an enormous memory hog).

The "uncloseable notification boxes" bug was fixed in a recent upstream release which hasn't landed on Dapper Drake (I don't know about Edgy).

---

### Post by gotgenes on 2006-10-04
> **Delkster said:**
> 
That said, for some reason the init script (to be run at system boot) created by Firestarter seems to fail for me so it doesn't actually set any rules, thus effectively leaving the firewall disabled. Issuing "sudo /etc/init.d/firestarter restart" later seems to work, though. I can't investigate the matter more now but it might be interesting to hear if you experience the same. You can check whether you have any firewalling enabled by commanding "sudo iptables -L", which lists all filtering rules given to the kernel. If it produces something like this, there are no rules:
```

$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

I experience this same bug in Firestarter. Are you using NetworkManager, too? Seems to be a bug. [https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/42759](https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/42759)

---

### Post by qsz on 2006-10-05
I'm trying to get the printer work now. I guess I have managed to get the driver installed because I can add the printer from System > Administration > Printing and there is a driver called i250-ver.2.3. The thing is nothing happens when I try to print.

Also when installing the printer, Ubuntu identifies two Canon i250's. One is *Canon i250 USB #1 (Canon i250)* and the other is *USB Printer #1 with status readback for Canon BJ (Canon i250)*. Neither of those works, the other printer says it's stopped and when using the other printer it just says 'ready' and nothing happens. I looked at the /var/log/cups/error_log and the error messages were 
> E [05/Oct/2006:18:29:52 +0300] cupsdAuthorize: Local authentication certificate not found!
E [05/Oct/2006:18:29:52 +0300] Resume-Printer: Unauthorized
E [05/Oct/2006:18:29:52 +0300] [Job 15] No %%BoundingBox: comment in header!
E [05/Oct/2006:18:29:52 +0300] [Job 15] Unable to open USB port device file: No such file or directory
E [05/Oct/2006:18:29:52 +0300] PID 11633 (/usr/lib/cups/backend/canon_usb) stopped with status 1!
E [05/Oct/2006:18:29:56 +0300] PID 11676 (/usr/lib/cups/backend/canon_usb) stopped with status 1!
E [05/Oct/2006:18:29:56 +0300] [Job 15] No %%BoundingBox: comment in header!
E [05/Oct/2006:18:29:56 +0300] [Job 15] Unable to open USB port device file: No such file or directory
and
> E [05/Oct/2006:18:33:32 +0300] CUPS-Add-Modify-Printer: Unauthorized
E [05/Oct/2006:18:33:45 +0300] [Job 16] No %%BoundingBox: comment in header!

and hundreds of rows of
E [05/Oct/2006:18:34:53 +0300] cupsdAuthorize: Local authentication certificate not found!

What could this mean?

---

### Post by qsz on 2006-11-02
I'm still having this problem with the printer. The problem is that my printer works fine in Windows Xp but in Ubuntu nothing happens. Printer status is always stopped and it can't be restarted. All files I print just go to the printer queue. Please help, all possible solutions are welcome.

---

