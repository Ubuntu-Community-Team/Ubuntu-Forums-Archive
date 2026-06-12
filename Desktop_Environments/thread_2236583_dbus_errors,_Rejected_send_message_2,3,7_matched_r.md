---
title: "dbus errors, Rejected send message 2,3,7 matched rules"
date: 2014-07-27
forum: Desktop Environments
---

### Post by richard_drilling on 2014-07-27
Hello everyone

kubuntu 14.04 (only os)
kde version: 4.13.2
grub  0.97-29ubuntu66 - GRand Unified Bootloader (Legacy version)


 
PC
Lenova ideapad z580
intel(R)Core(TM)i5-3210M CPU @ 2.50GHz 1200MHz 64-bit
ram 8gig
HDD 1@ 4OOGIG (internal)
GPU 00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
Optical Drives (1) Internal


Fairly new to linux, but have played around with  a few distros on vmware. I decided to move to linux and decided to try kubuntu 14.04. Every thing seemed to go well with installation however sometimes during boot up it hangs up before the kubuntu splash screen, and has to be mannualy restarted. Checking authlog, I have several dbus errors.
 I've been searching, forums, and google for this issue, and have'nt had much luck.

Here are a few lines with the error 

 rick-Lenovo-Z580    dbus[812]    [system] Rejected send message, 3 matched rules; type="error", sender=":1.51" (uid=1000 pid=2275 comm="/usr/bin/pulseaudio --start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.1" (uid=0 pid=869 comm="/usr/sbin/bluetoothd ")07/21/14 06:34:39 AM    rick-Lenovo-Z580    dbus[812]    message repeated 3 times: [ [system] Rejected send message, 3 matched rules; type="error", sender=":1.51" (uid=1000 pid=2275 comm="/usr/bin/pulseaudio --start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.1" (uid=0 pid=869 comm="/usr/sbin/bluetoothd ")]
07/21/14 06:34:39 AM    rick-Lenovo-Z580    dbus[812]    [system] Rejected send message, 3 matched rules; type="error", sender=":1.60" (uid=1000 pid=2375 comm="/usr/bin/pulseaudio --start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.1" (uid=0 pid=869 comm="/usr/sbin/bluetoothd ")
07/21/14 06:34:39 AM    rick-Lenovo-Z580    dbus[812]    message repeated 3 times: [ [system] Rejected send message, 3 matched rules; type="error", sender=":1.60" (uid=1000 pid=2375 comm="/usr/bin/pulseaudio --start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.1" (uid=0 pid=869 comm="/usr/sbin/bluetoothd ")]
07/21/14 06:34:39 AM    rick-Lenovo-Z580    dbus[812]    [system] Rejected send message, 3 matched rules; type="error", sender=":1.35" (uid=1000 pid=2121 comm="kdeinit4: kded4 [kdeinit]                       ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownObject" requested_reply="0" destination=":1.1" (uid=0 pid=869 comm="/usr/sbin/bluetoothd ")
07/21/14 06:35:14 AM    rick-Lenovo-Zbelow are a few lines of the auth log error.

dbus[812]    [system] Rejected send message, 3 matched rules; type="method_return", sender=":1.56" (uid=0 pid=2359 comm="/usr/bin/python /usr/share/apt-xapian-index/update") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.35" (uid=1000 pid=2121 comm="kdeinit4: kded4 [kdeinit]                       ")


--start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.1" (uid=0 pid=869 comm="/usr/sbin/bluetoothd ")
07/21/14 10:06:31 AM    rick-Lenovo-Z580    dbus[812]    [system] Rejected send message, 3 matched rules; type="error", sender=":1.51" (uid=1000 pid=2275 comm="/usr/bin/pulseaudio --start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.1" (uid=0 pid=869 comm="/usr/sbin/bluetoothd ")
07/21/14 10:06:31 AM    rick-Lenovo-Z580    dbus[812]    [system] Rejected send message, 3 matched rules; type="error", sender=":1.51" (uid=1000 pid=2275 comm="/usr/bin/pulseaudio --start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.1" (uid=0 pid=869 comm="/usr/sbin/bluetoothd ")
07/21/14 10:06:31 AM    rick-Lenovo-Z580    dbus[812]    [system] Rejected send message, 3 matched rules; type="error", sender=":1.60" (uid=1000 pid=2375 comm="/usr/bin/pulseaudio --start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.1" (uid=0 pid=869 comm="/usr/sbin/bluetoothd ")
07/21/14 10:06:31 AM    rick-Lenovo-Z580    dbus[812]    [system] Rejected send message, 3 matched rules; type="error", sender=":1.51" (uid=1000 pid=2275 comm="/usr/bin/pulseaudio --start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.1" (uid=0 pid=869 comm="/usr/sbin/bluetoothd ")
07/21/14 10:06:31 AM    rick-Lenovo-Z580    dbus[812]    [system] Rejected send message, 3 matched rules; type="error", sender=":1.51" (uid=1000 pid=2275 comm="/usr/bin/pulseaudio --start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.1" (uid=0 pid=869 comm="/usr/sbin/bluetoothd ")
07/21/14 10:06:31 AM    rick-Lenovo-Z580    dbus[812]    [system] Rejected send message, 3 matched rules; type="error", sender=":1.60" (uid=1000 pid=2375 comm="/usr/bin/pulseaudio --start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.1" (uid=0 pid=869 comm="/usr/sbin/bluetoothd ")
07/21/14 10:06:31 AM    rick-Lenovo-Z580    dbus[812]    [system] Rejected send message, 3 matched rules; type="error", sender=":1.60" (uid=1000 pid=2375 comm="/usr/bin/pulseaudio --start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.1" (uid=0 pid=869 comm="/usr/sbin/bluetoothd ")
07/21/14 10:06:31 AM    rick-Lenovo-Z580    dbus[812]    [system] Rejected send message, 3 matched rules; type="error", sender=":1.35" (uid=1000 pid=2121 comm="kdeinit4: kded4 [kdeinit]                       ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownObject" requested_reply="0" destination=":1.1" (uid=0 pid=869 comm="/usr/sbin/bluetoothd ")


rick-Lenovo-Z580    dbus[756]    [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.16" (uid=0 pid=1352 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=928 comm="NetworkManager ")

any help would

---

