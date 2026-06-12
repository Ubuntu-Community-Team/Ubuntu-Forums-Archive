---
title: "Desktop issues"
date: 2016-11-19
forum: Desktop Environments
---

### Post by helios-cobain-stefani on 2016-11-19
Greetings.

Recently installed an Ubuntu Studio distribution from 12.04 and upgraded it to 14.04, after upgrading some issues have appeared within the overall desktop UI, specifically:

-- xfce4-panel is presenting heavy latency at opening, while unresponsive after the first five clicks;
-- multiple desktops is presenting mouse jumping from desktop to desktop, without dragging any apparent window;
-- there are cursor jumps while writing, and window jumps while pointing.

I have installed and executed chkrootkit, which shows some suspicious files in python, jvm:

[FONT=courier new]Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/python2.7/dist-packages/PyQt4/uic/widget-plugins/.noinit /usr/lib/jvm/.java-1.7.0-openjdk-i386.jinfo /usr/lib/jvm/.java-1.6.0-openjdk-i386.jinfo /usr/lib/pymodules/python2.7/.path
[/FONT]
Besides, a Suckit appearant infection -which could be a false alarm, as i have read around-, a couple of packet sniffers, and some temporal user tty issue:

[FONT=courier new]Searching for Suckit rootkit...                             Warning: /sbin/init INFECTED

Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[1080], /sbin/dhclient[2423])

Checking `chkutmp'...                                        The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! root         1731 tty7   /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[/FONT]
I have also installed and runned rkhunter, which shows a few "[Warning]" and "[skipped]" messages:

[FONT=courier new]    /usr/bin/unhide.rb                                       [ Warning ]

    Checking for hidden ports                                [ Skipped ]

    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]
[/FONT]
I tryed upgrading all the way upto Ubuntu Studio 16.04 before, but there seems to be lack of support for my equipment processor (Intel Atom) to install from scratch, and a recurrent bug which avoids the system from starting and loggin in by switching to sleep mode over and over, after upgrading. I was able to login through x11 by "awaking" the system each time it went asleep and introducing the password at a speed faster than the time it periodically switchs to sleep mode (about half of a minute), yet, it had to be logged in perpetually without rebooting, otherwise i had to be 'fast enough' to get in. As such, after a few upgradings and reboots i had to came back to Ubuntu Studio 12.04 and upgrade to 14.04 in order to keep overall operativity as i run an audiovisual studio and there's the constant need not to interrupt operativity.

Thanks in advance.

---

### Post by Autodave on 2016-11-19
I have RARELY had any luck upgrading from one version to another. I back up everything and do a fresk install.  And, while you are at it, use 16.04: the newest long term release.

---

