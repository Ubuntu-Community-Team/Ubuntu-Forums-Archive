---
title: "DSL-500B Router - hacking"
date: 2009-05-04
forum: General Help
---

### Post by trigsenior on 2009-05-04
Hello , 


I recently acquired a DSL-500B Router. I have been over the last few weeks
trying to hack it and in hack I mean do things it was not originally suppose to do. Here are the router system properties..  


               total:       used:         free:         shared:     buffers:
Mem:           6108         5800          308            0          160
Swap:            0            0            0
-----------------------------------------------------------------------
Total:         6108         5800          308



cat /proc/cpuinfo

system type             : 96338L-2M-8M
processor               : 0
cpu model               : BCM6338 V1.0
BogoMIPS                : 239.20
wait instruction        : no
microsecond timers      : yes
tlb_entries             : 32
extra interrupt vector  : yes
hardware watchpoint     : no
VCED exceptions         : not available
VCEI exceptions         : not available


cat /proc/version

Linux version 2.6.8.1 (root@localhost.localdomain) (gcc version 3.4.2) #2 Tue Apr 17 17:18:41 CST 2007


I have following tools..

Default tools

?
help
logout
reboot
adsl
atm
brctl
cat
ddns
df
dumpcfg
echo
ifconfig
kill
arp
defaultgateway
dhcpserver
dns
lan
passwd
ppp
remoteaccess
restoredefault
route
save
swversion
wan
ping
ps
pwd
macaddr
sntp
sysinfo
tftp

I was also able to get at hidden busy-box commands through typing sh.
( took me a long time to find out )

Built-in commands:
-------------------
        . : break cd continue eval exec exit export help login newgrp
        read readonly set shift times trap umask wait [ busybox cat chmod
        date df dmesg echo expr false ftpget ifconfig init insmod kill
        klogd linuxrc ln logger logread mkdir mount msh ping ps pwd reboot
        rm rmmod route sendarp sh sysinfo syslogd test tftp tftpd top
        true tty vconfig





I want to edit /webs directory , as would be great to set this as up a server .. not to mention would love to install couple small programs ( this possible ? )  ;)


However I can not edit the /webs directory because  it is an embeded device / router they have decided that the /webs directory does not need 
rw so as to save space they  have squashfs  it making it only ro . I think this is what has happened anyway. I have tried using chmod but i get read only error. Here is what baffles me , if it is a squashfs directory then surly in /etc/fstab  and mount it would indicate /webs ? 
As at every reboot the directory would have to re mounted ?

Here is mount command.

/dev/mtdblock0 on / type squashfs (ro)
/proc on /proc type proc (rw,nodiratime)
tmpfs on /var type tmpfs (rw)



here is /etc/fstab 

cat /etc/fstab
proc            /proc   proc    defaults        0       0
tmpfs           /var    tmpfs   size=320k       0       0
/dev/sda1       /mnt    vfat    noauto          0       0


cat /proc/mounts

rootfs / rootfs rw 0 0
/dev/root / squashfs ro 0 0
/proc /proc proc rw,nodiratime 0 0
tmpfs /var tmpfs rw 0 0

cat /proc/filesystems 
nodev   rootfs
nodev   bdev
nodev   proc
nodev   sockfs
nodev   tmpfs
nodev   pipefs
        squashfs
nodev   ramfs




If anyone could shed light on this phenomenon I would be eternity grateful.

Also I know this is probably in the wrong topic as it not at all 
ubuntu related I just thought someone might know. 

Also does anyone know a nc/telnet program that does not auto log off after 3 minutes ?

trigsenior

---

### Post by salvachn on 2009-05-14
DSL Router OK. What Brand? Mine is D-Link GLB-802C. I'd also love to the same with it.

---

### Post by trigsenior on 2009-05-26
Sorry for slow reply ,

I have a Dlink aswell here more info 

BoardID:  	DSL-500B
Software Version: 	BCM-1.1.BR.20060205_a
Bootloader (CFE) Version: 	1.0.37-0.8

---

