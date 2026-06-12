---
title: "How can Do to make boot faster?"
date: 2005-06-02
forum: Desktop Environments
---

### Post by lizardking on 2005-06-02
**How can Do to make boot faster?**

I installed **samba **and** hotplug**. Hotplug is so slowly.
I was thinikng to remove Hotplug from the boot and only when I use USB i can run it **manually by console..**

But I don't Know how to clear Hotplug from boot. Instaed I can stop restart It with
```
 /etc/init.d/hotplug {start|stop|restart|status|force-reload}
``` 
this are my script in **/etc/init.d** 
```
lizardking@iac:~ $ /etc/init.d/
acpid              cupsys             hotplug            mdadm-raid         pppd-dns           screen-cleanup
acpi-support       dbus-1             hwclockfirst.sh    module-init-tools  procps.sh          sendsigs
alsa               discover           hwclock.sh         modutils           progress.kernel    single
apache2            dns-clean          ifupdown           mountall.sh        progress.mount     skeleton
apmd               evms               inetd              mountnfs.sh        progress.network   stop-bootlogd
atd                failed             initrd-tools.sh    mountvirtfs        progress.service   sudo
binfmt-support     failed.d           jove               networking         progress.up        sysklogd
bootlogd           fam                keymap.sh          ntpdate            rc                 udev
bootmisc.sh        fetchmail          klogd              nvidia-glx         rcS                umountfs
checkfs.sh         gdm                libdevmapper1.00   portmap            reboot             umountnfs.sh
checkroot.sh       halt               lvm                postfix            rmnologin          urandom
console-screen.sh  hdparm             makedev            powernowd          rsync              xfree86-common
cron               hostname.sh        mdadm              ppp                samba
```[FONT=Tahoma]**Someone knows how to take off hotplug from start? [init.d]**[/FONT]

---

### Post by defkewl on 2005-06-02
$ update-rc.d -f hotplug remove

---

### Post by nocturn on 2005-06-02
install rcconf (apt-get install rcconf).
Run rcconf as root (sudo rcconf)

Uncheck hotplug, Done.

---

### Post by bored2k on 2005-06-02
sudo chmod -x /etc/init.d/hotplug
sudo chmod -x /etc/init.d/ntpdate

That would speed up things.

---

### Post by Alexander Kirillov on 2005-06-02
[http://ubuntuguide.org/#permanentlydisableenableboot-upservices](http://ubuntuguide.org/#permanentlydisableenableboot-upservices)

But hotplug is not supposed to be slow - if it is, it is an indication that something is wrong with you setup or hardware. I'd suggest finding it out and fixing, rather than disabling hotplug.

---

### Post by lizardking on 2005-06-02
[QUOTE=nocturn]install rcconf (apt-get install rcconf).
Run rcconf as root (sudo rcconf)

Uncheck hotplug, Done.[/QUOTE]
No Hotplug Ther isn't in rcconf  [-X

---

### Post by lizardking on 2005-06-02
[QUOTE=defkewl]$ update-rc.d -f hotplug remove[/QUOTE]
And to take back htoplug in case I wanto to re-enable that??

---

### Post by lizardking on 2005-06-02
](*,)  **Nooo if I stop Hotplug that disable my integrated sound card. So I cannot take off Hoplug... My booot is so slow....** ](*,)

---

### Post by jazzer on 2005-06-08
Actually, the hotplug in warty is also slow on my computer.  However, I updated it using the backports repository to the Hoary version and it's much faster now.  So I would try upgrading your version of hotplug using the backports version.

---

