---
title: "Mysterious error message just after start"
date: 2005-07-02
forum: Desktop Environments
---

### Post by niels2005 on 2005-07-02
dear ubuntupeople,
I am getting an error message saying (translated from german in english: no command introduced to be performed) just after bootup and starting gnome (in kubuntu session there is no message), I cannot explain why this happens (crossover uninstalled and reinstalled, recent installed packages uninstalled, apt-get update done no prob),
it seems that gnome expects a command and does not get one ?!?
if i just close the window nothing bad happens,
it is just very annoying,
can anyone help ??? ](*,) 
niels

hoary 5.05
on dell510m

---

### Post by angkor on 2005-07-02
I think a read somewhere it had to do with Gdesklets...I'll try to find the link

---

### Post by niels2005 on 2005-07-03
I checked for this: /etc/rc2.d
is there something strange to anyone that I get the error message from above ?

K09samba          S12alsa    S20gnump3d    S25mdadm           S99fetchmail
K11anacron        S13gdm     S20inetd      S50proftpd         S99rmnologin
K77ntp-server     S14ppp     S20makedev    S89anacron         S99stop-bootlogd
S05vbesave        S19cupsys  S20pcmcia     S89atd
S09startupscript  S20acpid   S20postfix    S89cron
S10sysklogd       S20apmd    S20powernowd  S90binfmt-support
S11klogd          S20dbus-1  S20rsync      S99acpi-support
niels@ubuntu:/etc/rc2.d$

niels

---

