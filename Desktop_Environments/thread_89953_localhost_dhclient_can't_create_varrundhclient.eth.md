---
title: "localhost dhclient can't create /var/run/dhclient.eth0.leases: Permission denied"
date: 2005-11-13
forum: Desktop Environments
---

### Post by jchau on 2005-11-13
I see this error on my syslog and daemon.log often:
> localhost dhclient can't create /var/run/dhclient.eth0.leases: Permission denied

dhclient3 is running as user dhcp according to System Monitor and the Arguments according to System Monitor is
dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/run/dhclient.eth0.leases eth0

not sure if the "-lf" in that is an I(eye) or a l(ell).  

doing ls -la /var/run/dhclient.eth0.*
returns
> -rw-r--r--  1 root root 11529 2005-11-13 19:13 /var/run/dhclient.eth0.leases
-rw-r--r--  1 root root     5 2005-11-13 14:48 /var/run/dhclient.eth0.pid

do I have to chown these files to user dhcp? chgrp? Should I make dhclient3 run as root instead of dhcp?  What is the problem?  will reinstalling the dhcp client fix it?  Are my permissions different from the default (i dont remember changing them)?

If this might help, I installed ddclient for dyndns before I noticed these problems.  

Thanks.  
-Jimmy

Note: simply reinstalling doesn't fix the problem.  Should I do a complete uninstall and then install?

---

### Post by mgor on 2005-11-14
hm, that's strange. the file permissions are the default, so there's nothing wrong with them. i checked my daemon.log and didn't see any permission errors.

seem to me it's a very simple error, so re-installing just because you'll think it'll solve it is so wrong :-) if you should re-installing something it might be enough re-installing dhclient ...

but do you get an ip adress even though you recevie the error? don't fix things that's working ..

---

### Post by jchau on 2005-11-19
Sorry, but I want to bump this thread up.  The error mesgs that dhclient3 is putting in my logs come so often that I see the following once every three lines:

localhost dhclient can't create /var/run/dhclient.eth0.leases: Permission denied

I tried reinstalling dhcp3-client and dhcp3-common and that does not help.  If I reboot my computer, the error messages don't start showing up in my logs for a few hours.  

chowning the /var/run/dhclient.eth0.leases file to user dhcp stops the error messages from showing up on my logs, but everytime I restart, and wait a few hours, the mesages start coming again.  Will it be safe in terms of security to chown this file? It was owned by root before

I looked around online and it seems like other people have this file in /var/lib, where it remains after restarting, so the info and the file-permssions stays the same.  Should have dhclient3 use the /var/lib directory instead?  What is the benefit of having the lease file in /var/run as opposed to /var/run?  

Oh, if I do this, and dhclient3 starts up with the computer.  How can I make dhclient3 put the lease file in /var/lib/dhcp3/ instead on startup?  I can see using > ps aux | grep "dhclient3" that the command > dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/run/dhclient.eth0.leases eth0 is running.  What starts this command and how can I edit the -lf argument?  

Is there any other way to fix this problem?

If this helps, /etc/dhcp3/dhclient.conf contains:
> # Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}


-thanks again
Jimmy

---

### Post by finnjimm on 2005-12-06
I have exactly the same problem on Kubuntu 5.10. It's a PITA especially since dhclient renews the ip every 30 seconds or so, making my logs full of those messages.

---

### Post by nick58b on 2005-12-12
Had a report of this bug, and then noticed it on several other of my machines as well. Looks like it's in bugzilla already:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=20553](https://bugzilla.ubuntu.com/show_bug.cgi?id=20553)

---

### Post by Al_maverick on 2006-01-05
I have the same problem in Kubuntu 5.10. Ethernet is working fine, though. Its just a PITA to have the daemon.log filled up with these errors.

---

### Post by jchau on 2006-02-21
Well, thanks for all the attn! Much appreciated :). I wrote a temporary fix for it.
I inserted the following into /etc/init.d/bootmisc.sh:
```
#
#       Set permissions on /var/run/dhclient.eth0.leases
#       created by Jimmy Chau
#
touch /var/run/dhclient.eth0.leases
chown dhcp /var/run/dhclient.eth0.leases
```

This gives ownership of the lease file to dhcp.  My /etc/init.d/bootmisc.sh is:
```
#
# bootmisc.sh   Miscellaneous things to be done during bootup.
#
# Version:      @(#)bootmisc.sh  2.85-17  04-Jun-2004  miquels@cistron.nl
#

DELAYLOGIN=yes
VERBOSE=yes
EDITMOTD=yes
[ -f /etc/default/rcS ] && . /etc/default/rcS

#
#       Put a nologin file in /etc to prevent people from logging in
#       before system startup is complete.
#
if [ "$DELAYLOGIN" = yes ]
then
        echo "System bootup in progress - please wait" > /etc/nologin
fi

#
#       Create /var/run/utmp so we can login.
#
: > /var/run/utmp
if grep -q ^utmp: /etc/group
then
        chmod 664 /var/run/utmp
        chgrp utmp /var/run/utmp
fi

#
#       Set pseudo-terminal access permissions.
#
if [ ! -e /dev/.devfsd ] && [ -c /dev/ttyp0 ]
then
        chmod -f 666 /dev/tty[p-za-e][0-9a-f]
        chown -f root:tty /dev/tty[p-za-e][0-9a-f]
fi

#
#       Set permissions on /var/run/dhclient.eth0.leases
#       created by Jimmy Chau
#
touch /var/run/dhclient.eth0.leases
chown dhcp /var/run/dhclient.eth0.leases

#
#       Update /etc/motd. If it's a symbolic link, do the actual work
#       in the directory the link points to.
#
if [ "$EDITMOTD" != no ]
then
        MOTD="`readlink -f /etc/motd || :`"
        if [ "$MOTD" != "" ]
        then
                uname -a > $MOTD.tmp
                sed 1d $MOTD >> $MOTD.tmp
                mv $MOTD.tmp $MOTD
        fi
fi

#
#       Save kernel messages in /var/log/dmesg
#
if [ -x /bin/dmesg ] || [ -x /sbin/dmesg ]
then
        dmesg -s 524288 > /var/log/dmesg
elif [ -c /dev/klog ]
then
        dd if=/dev/klog of=/var/log/dmesg &
        dmesg_pid=$!
        sleep 1
        kill $dmesg_pid
fi


#
#       Remove ".clean" files.
#
rm -f /tmp/.clean /var/run/.clean /var/lock/.clean

: exit 0


```

Add other files as necessary.  There is no reason why a file that only dhcp uses should not be owned by dhcp.  

Once again, here is a late thanks (I haven't been checking this thread of mine often).

---

