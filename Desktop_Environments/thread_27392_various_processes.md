---
title: "various processes"
date: 2005-04-15
forum: Desktop Environments
---

### Post by jhands on 2005-04-15
how can i find out what processes are running on my computer and i want to know which ones can i stop without affecting ubuntu's functioning. my desktop seems pretty. slow. iz there any way to find what processes run during boot ?

---

### Post by speedman on 2005-04-15
ls /etc/rc2.d/

ls /etc/rcS.d/

... will show you what services/daemons are launched on boot.

Depending on your system there are a handful that can be turned off.


Regards,

SM

---

### Post by crane on 2005-04-16
You could also open a terminal window and type 
top

that would give a list of what processes are using what recources.

---

### Post by jhands on 2005-04-16
these are the pictures of the various processes that run at boot and the other one is of current running processes. can any one tell me which ones and how can i turn some of them off safely and also that they wont start at bootup again

[[IMG]http://img153.echo.cx/img153/6231/screenshot35fi.th.png[/IMG]](http://img153.echo.cx/my.php?image=screenshot35fi.png)

[[IMG]http://img183.echo.cx/img183/1782/screenshot43tg.th.png[/IMG]](http://img183.echo.cx/my.php?image=screenshot43tg.png)

---

### Post by jhands on 2005-04-16
*bump"

---

### Post by tread on 2005-04-16
Install sysv-rc-conf (do an apt-get or install via synaptic) .. then run it as a superuser. You will see a number of services listed in different runlevels .. you can just turn off the ones you dont need. 

In case you don't know, runlevels decide what services are started at boot, now the question to ask here is: which runlevel should i edit? I don't know that .. but looking back in this thread it might be 2. Anyway, some processes you can disable in all runlevels .. like I did with ppp (since I don't need it .. I think :))

Hope that helps!

---

### Post by speedman on 2005-04-17
The default run level for Debian is 2 and the corresponding init script links are in /etc/rc2.d.  However, /etc/rcS.d/ also contains init script links that are launched in every run level.

Anything that starts with a Kxx does not run on boot and anything that starts with a Sxx does.

To give you an idea of what is configured on my laptop for daemons launched at boot time;

chris@i8500:~ $ ls /etc/rc2.d/
K11anacron    K99mdadm      K99samba     S19cupsys      S20ssh
K99apmd       K99openvpn    S05vbesave   S20acpid       S89anacron
K99atd        K99postfix    S10sysklogd  S20dbus-1      S89cron
K99fetchmail  K99powernowd  S11klogd     S20makedev     S99acpi-support
K99hddtemp    K99ppp        S12alsa      S20nvidia-glx  S99rmnologin
K99inetd      K99rsync      S13gdm       S20pcmcia      S99stop-bootlogd

chris@i8500:~ $ ls /etc/rcS.d/
K99evms         S05initrd-tools.sh    S30splashy30          S50hwclock.sh
K99lm-sensors   S05keymap.sh          S35mountall.sh        S50splashy50
K99lvm          S07hdparm             S36mountvirtfs        S55bootmisc.sh
K99mdadm-raid   S10checkroot.sh       S36udev-mtab          S55urandom
K99mountnfs.sh  S10splashy10          S39dns-clean          S60splashy60
K99ntpdate      S18hwclockfirst.sh    S39ifupdown           S70screen-cleanup
K99pppd-dns     S18ifupdown-clean     S39readahead          S70splashy70
README          S20module-init-tools  S40hostname.sh        S70xorg-common
S01splashy      S20splashy20          S40hotplug            S75sudo
S02mountvirtfs  S25libdevmapper1.00   S40networking
S04udev         S30checkfs.sh         S40splashy40
S05bootlogd     S30procps.sh          S48console-screen.sh

The console app rcconf is probably the easiest way for you to address service management:

sudo apt-get install rcconf

sudo rcconf

Most of the daemons listed in the init directories have corresponding man page entries and if they don't you can easily read their contents as they are just shell scripts.  Of course google is your friend too.

HTH


Regards,

SM

---

