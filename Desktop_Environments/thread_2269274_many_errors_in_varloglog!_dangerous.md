---
title: "many errors in /var/log/*log! dangerous?"
date: 2015-03-14
forum: Desktop Environments
---

### Post by siggi2 on 2015-03-14
Hi,

I am on Ubuntu 14.04 Unity amd64. When I use the command *sudo egrep -i 'error|warning' /var/log/*log* I see a lot of error warnings! Should I be worried?

Here is the output into a textfile:

```
sudo egrep -i 'error|warning' /var/log/*log > logErrors20150314.txt:

/var/log/auth.log:Mar 10 11:22:29 myown-Desktop dbus[685]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.13" (uid=0 pid=1018 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=735 comm="NetworkManager ")
/var/log/auth.log:Mar 10 11:36:55 myown-Desktop sudo:  myown : TTY=pts/0 ; PWD=/home/myown ; USER=root ; COMMAND=/bin/egrep -i error|warning /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/pm-powersave.log /var/log/pm-suspend.log /var/log/prime-offload.log /var/log/prime-supported.log /var/log/syslog /var/log/Xorg.0.log /var/log/Xorg.1.log /var/log/Xorg.2.log /var/log/Xorg.failsafe.log
/var/log/auth.log:Mar 10 11:52:08 myown-Desktop dbus[670]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.12" (uid=0 pid=1398 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=735 comm="NetworkManager ")
/var/log/auth.log:Mar 11 13:49:55 myown-Desktop dbus[684]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.78" (uid=0 pid=3037 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=732 comm="NetworkManager ")
/var/log/auth.log:Mar 11 13:50:16 myown-Desktop dbus[684]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.78" (uid=0 pid=3037 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=732 comm="NetworkManager ")
/var/log/auth.log:Mar 11 13:51:56 myown-Desktop dbus[684]: [system] Rejected send message, 2 matched rules; type="error", sender=":1.4" (uid=0 pid=732 comm="NetworkManager ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.83" (uid=0 pid=3256 comm="/usr/sbin/pppd nodetach lock nodefaultroute ipv6 ,")
/var/log/auth.log:Mar 11 13:52:35 myown-Desktop dbus[684]: [system] Rejected send message, 2 matched rules; type="error", sender=":1.4" (uid=0 pid=732 comm="NetworkManager ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.84" (uid=0 pid=3278 comm="/usr/sbin/pppd nodetach lock nodefaultroute ipv6 ,")
/var/log/auth.log:Mar 11 13:52:36 myown-Desktop dbus[684]: message repeated 3 times: [ [system] Rejected send message, 2 matched rules; type="error", sender=":1.4" (uid=0 pid=732 comm="NetworkManager ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.84" (uid=0 pid=3278 comm="/usr/sbin/pppd nodetach lock nodefaultroute ipv6 ,")]
/var/log/auth.log:Mar 11 13:59:56 myown-Desktop dbus[684]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.77" (uid=0 pid=2945 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=733 comm="NetworkManager ")
/var/log/auth.log:Mar 11 14:00:01 myown-Desktop dbus[684]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.77" (uid=0 pid=2945 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=733 comm="NetworkManager ")
/var/log/auth.log:Mar 11 14:00:35 myown-Desktop dbus[684]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.77" (uid=0 pid=2945 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=733 comm="NetworkManager ")
/var/log/auth.log:Mar 11 14:00:39 myown-Desktop dbus[684]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.77" (uid=0 pid=2945 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=733 comm="NetworkManager ")
/var/log/auth.log:Mar 11 22:18:42 myown-Desktop dbus[687]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.86" (uid=0 pid=3026 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.3" (uid=0 pid=758 comm="NetworkManager ")
/var/log/auth.log:Mar 12 16:09:27 myown-Desktop dbus[686]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.86" (uid=0 pid=3194 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=736 comm="NetworkManager ")
/var/log/auth.log:Mar 12 16:10:38 myown-Desktop gnome-keyring-daemon[2239]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
/var/log/auth.log:Mar 12 16:11:12 myown-Desktop gnome-keyring-daemon[3881]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
/var/log/auth.log:Mar 12 17:03:15 myown-Desktop dbus[686]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.86" (uid=0 pid=3194 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=736 comm="NetworkManager ")
/var/log/auth.log:Mar 12 20:42:47 myown-Desktop lightdm: pam_winbind(lightdm:auth): internal module error (retval = PAM_AUTHINFO_UNAVAIL(9), user = 'myown')
/var/log/auth.log:Mar 12 20:42:53 myown-Desktop gnome-keyring-daemon[1512]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
/var/log/auth.log:Mar 12 20:45:13 myown-Desktop sudo:  myown : TTY=pts/0 ; PWD=/home/myown ; USER=root ; COMMAND=/bin/egrep -i error|warning /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/pm-powersave.log /var/log/pm-suspend.log /var/log/prime-offload.log /var/log/prime-supported.log /var/log/syslog /var/log/Xorg.0.log /var/log/Xorg.1.log /var/log/Xorg.2.log /var/log/Xorg.failsafe.log
/var/log/auth.log:Mar 12 20:46:36 myown-Desktop dbus[713]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.80" (uid=0 pid=3254 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=788 comm="NetworkManager ")
/var/log/auth.log:Mar 12 21:11:56 myown-Desktop dbus[716]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.79" (uid=0 pid=2857 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=764 comm="NetworkManager ")
/var/log/auth.log:Mar 12 21:41:30 myown-Desktop dbus[712]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.83" (uid=0 pid=3264 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=784 comm="NetworkManager ")
/var/log/auth.log:Mar 12 21:41:38 myown-Desktop sudo:  myown : TTY=pts/1 ; PWD=/home/myown ; USER=root ; COMMAND=/bin/egrep -i error|warning /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/pm-powersave.log /var/log/pm-suspend.log /var/log/prime-supported.log /var/log/syslog /var/log/Xorg.0.log /var/log/Xorg.1.log /var/log/Xorg.2.log /var/log/Xorg.failsafe.log
/var/log/auth.log:Mar 13 08:53:34 myown-Desktop dbus[683]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.82" (uid=0 pid=3200 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.3" (uid=0 pid=823 comm="NetworkManager ")
/var/log/auth.log:Mar 13 08:54:51 myown-Desktop polkit-agent-helper-1[3407]: pam_winbind(polkit-1:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
/var/log/auth.log:Mar 13 08:59:37 myown-Desktop sudo:  myown : TTY=pts/10 ; PWD=/home/myown ; USER=root ; COMMAND=/bin/egrep -i error|warning /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/pm-powersave.log /var/log/pm-suspend.log /var/log/prime-offload.log /var/log/prime-supported.log /var/log/syslog /var/log/Xorg.0.log /var/log/Xorg.1.log /var/log/Xorg.2.log /var/log/Xorg.failsafe.log
/var/log/auth.log:Mar 13 09:05:41 myown-Desktop dbus[686]: [system] Rejected send message, 2 matched rules; type="error", sender=":1.4" (uid=0 pid=766 comm="NetworkManager ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.94" (uid=0 pid=3458 comm="/usr/sbin/pppd nodetach lock nodefaultroute ipv6 ,")
/var/log/auth.log:Mar 13 09:05:42 myown-Desktop dbus[686]: [system] Rejected send message, 2 matched rules; type="error", sender=":1.4" (uid=0 pid=766 comm="NetworkManager ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.94" (uid=0 pid=3458 comm="/usr/sbin/pppd nodetach lock nodefaultroute ipv6 ,")
/var/log/auth.log:Mar 13 09:06:29 myown-Desktop dbus[686]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.97" (uid=0 pid=3637 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=766 comm="NetworkManager ")
/var/log/auth.log:Mar 13 09:16:54 myown-Desktop gnome-keyring-daemon[2243]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
/var/log/auth.log:Mar 13 09:16:54 myown-Desktop dbus[686]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.97" (uid=0 pid=3637 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=766 comm="NetworkManager ")
/var/log/auth.log:Mar 13 09:18:35 myown-Desktop dbus[686]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.97" (uid=0 pid=3637 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=766 comm="NetworkManager ")
/var/log/auth.log:Mar 13 09:20:07 myown-Desktop sudo:     nati : user NOT in sudoers ; TTY=pts/0 ; PWD=/home/nati ; USER=root ; COMMAND=/bin/egrep -i error|warning /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/pm-powersave.log /var/log/pm-suspend.log /var/log/prime-offload.log /var/log/prime-supported.log /var/log/syslog /var/log/Xorg.0.log /var/log/Xorg.1.log /var/log/Xorg.2.log /var/log/Xorg.failsafe.log
/var/log/auth.log:Mar 13 09:24:20 myown-Desktop dbus[686]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.97" (uid=0 pid=3637 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=766 comm="NetworkManager ")
/var/log/auth.log:Mar 13 09:24:20 myown-Desktop dbus[686]: [system] Rejected send message, 2 matched rules; type="error", sender=":1.4" (uid=0 pid=766 comm="NetworkManager ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.162" (uid=0 pid=5240 comm="/usr/sbin/pppd nodetach lock nodefaultroute ipv6 ,")
/var/log/auth.log:Mar 13 09:24:20 myown-Desktop dbus[686]: message repeated 3 times: [ [system] Rejected send message, 2 matched rules; type="error", sender=":1.4" (uid=0 pid=766 comm="NetworkManager ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.162" (uid=0 pid=5240 comm="/usr/sbin/pppd nodetach lock nodefaultroute ipv6 ,")]
/var/log/auth.log:Mar 13 09:24:21 myown-Desktop dbus[686]: [system] Rejected send message, 2 matched rules; type="error", sender=":1.4" (uid=0 pid=766 comm="NetworkManager ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.162" (uid=0 pid=5240 comm="/usr/sbin/pppd nodetach lock nodefaultroute ipv6 ,")
/var/log/auth.log:Mar 13 09:24:33 myown-Desktop dbus[686]: [system] Rejected send message, 3 matched rules; type="error", sender=":1.144" (uid=1001 pid=4544 comm="/usr/bin/pulseaudio --start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.1" (uid=0 pid=709 comm="/usr/sbin/bluetoothd ")
/var/log/auth.log:Mar 13 09:24:33 myown-Desktop dbus[686]: message repeated 3 times: [ [system] Rejected send message, 3 matched rules; type="error", sender=":1.144" (uid=1001 pid=4544 comm="/usr/bin/pulseaudio --start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.1" (uid=0 pid=709 comm="/usr/sbin/bluetoothd ")]
/var/log/auth.log:Mar 13 09:26:50 myown-Desktop dbus[686]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.97" (uid=0 pid=3637 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=766 comm="NetworkManager ")
/var/log/auth.log:Mar 13 13:12:43 myown-Desktop compiz: pam_winbind(lightdm:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
/var/log/auth.log:Mar 13 16:17:42 myown-Desktop gnome-keyring-daemon[4297]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
/var/log/auth.log:Mar 13 16:17:44 myown-Desktop dbus[686]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.97" (uid=0 pid=3637 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=766 comm="NetworkManager ")
/var/log/auth.log:Mar 13 16:19:49 myown-Desktop sudo:  myown : TTY=pts/0 ; PWD=/home/myown ; USER=root ; COMMAND=/bin/egrep -i error|warning /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/pm-powersave.log /var/log/pm-suspend.log /var/log/prime-offload.log /var/log/prime-supported.log /var/log/syslog /var/log/Xorg.0.log /var/log/Xorg.1.log /var/log/Xorg.2.log /var/log/Xorg.failsafe.log
/var/log/auth.log:Mar 13 16:25:23 myown-Desktop dbus[686]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.97" (uid=0 pid=3637 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=766 comm="NetworkManager ")
/var/log/auth.log:Mar 13 17:11:54 myown-Desktop dbus[686]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.97" (uid=0 pid=3637 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=766 comm="NetworkManager ")
/var/log/auth.log:Mar 13 17:12:56 myown-Desktop dbus[686]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.97" (uid=0 pid=3637 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=766 comm="NetworkManager ")
/var/log/auth.log:Mar 13 17:16:51 myown-Desktop dbus[686]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.97" (uid=0 pid=3637 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=766 comm="NetworkManager ")
/var/log/auth.log:Mar 13 17:17:01 myown-Desktop gnome-keyring-daemon[9676]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
/var/log/auth.log:Mar 13 17:32:23 myown-Desktop dbus[697]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.91" (uid=0 pid=2968 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=762 comm="NetworkManager ")
/var/log/auth.log:Mar 13 17:33:19 myown-Desktop sudo:  myown : TTY=pts/0 ; PWD=/home/myown ; USER=root ; COMMAND=/bin/egrep -i error|warning /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/pm-powersave.log /var/log/pm-suspend.log /var/log/prime-offload.log /var/log/prime-supported.log /var/log/syslog /var/log/Xorg.0.log /var/log/Xorg.1.log /var/log/Xorg.2.log /var/log/Xorg.failsafe.log
/var/log/auth.log:Mar 13 18:02:45 myown-Desktop polkit-agent-helper-1[4650]: pam_winbind(polkit-1:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
/var/log/auth.log:Mar 13 18:13:54 myown-Desktop dbus[697]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.91" (uid=0 pid=2968 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=762 comm="NetworkManager ")
/var/log/auth.log:Mar 13 18:31:12 myown-Desktop dbus[713]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.91" (uid=0 pid=2966 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.3" (uid=0 pid=755 comm="NetworkManager ")
/var/log/auth.log:Mar 13 18:32:00 myown-Desktop dbus[713]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.91" (uid=0 pid=2966 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.3" (uid=0 pid=755 comm="NetworkManager ")
/var/log/auth.log:Mar 13 18:32:57 myown-Desktop dbus[713]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.91" (uid=0 pid=2966 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.3" (uid=0 pid=755 comm="NetworkManager ")
/var/log/auth.log:Mar 13 18:46:57 myown-Desktop dbus[713]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.91" (uid=0 pid=2966 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.3" (uid=0 pid=755 comm="NetworkManager ")
/var/log/auth.log:Mar 13 20:00:35 myown-Desktop dbus[693]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.93" (uid=0 pid=3139 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.3" (uid=0 pid=755 comm="NetworkManager ")
/var/log/auth.log:Mar 13 21:09:43 myown-Desktop dbus[693]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.93" (uid=0 pid=3139 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.3" (uid=0 pid=755 comm="NetworkManager ")
/var/log/auth.log:Mar 13 21:09:43 myown-Desktop dbus[693]: [system] Rejected send message, 2 matched rules; type="error", sender=":1.3" (uid=0 pid=755 comm="NetworkManager ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.91" (uid=0 pid=3113 comm="/usr/sbin/pppd nodetach lock nodefaultroute ipv6 ,")
/var/log/auth.log:Mar 14 09:56:56 myown-Desktop lightdm: pam_winbind(lightdm:auth): internal module error (retval = PAM_AUTHINFO_UNAVAIL(9), user = 'myown')
/var/log/auth.log:Mar 14 09:58:20 myown-Desktop dbus[714]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.79" (uid=0 pid=3010 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=772 comm="NetworkManager ")
/var/log/auth.log:Mar 14 10:04:00 myown-Desktop dbus[714]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.79" (uid=0 pid=3010 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=772 comm="NetworkManager ")
/var/log/auth.log:Mar 14 10:07:28 myown-Desktop dbus[714]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.79" (uid=0 pid=3010 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=772 comm="NetworkManager ")
/var/log/auth.log:Mar 14 10:18:22 myown-Desktop gnome-keyring-daemon[2337]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
/var/log/auth.log:Mar 14 10:18:22 myown-Desktop dbus[714]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.79" (uid=0 pid=3010 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=772 comm="NetworkManager ")
/var/log/auth.log:Mar 14 10:18:22 myown-Desktop dbus[714]: [system] Rejected send message, 2 matched rules; type="error", sender=":1.5" (uid=0 pid=772 comm="NetworkManager ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.85" (uid=0 pid=3521 comm="/usr/sbin/pppd nodetach lock nodefaultroute ipv6 ,")
/var/log/auth.log:Mar 14 10:18:22 myown-Desktop dbus[714]: message repeated 3 times: [ [system] Rejected send message, 2 matched rules; type="error", sender=":1.5" (uid=0 pid=772 comm="NetworkManager ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.85" (uid=0 pid=3521 comm="/usr/sbin/pppd nodetach lock nodefaultroute ipv6 ,")]
/var/log/auth.log:Mar 14 10:18:23 myown-Desktop dbus[714]: [system] Rejected send message, 2 matched rules; type="error", sender=":1.5" (uid=0 pid=772 comm="NetworkManager ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.85" (uid=0 pid=3521 comm="/usr/sbin/pppd nodetach lock nodefaultroute ipv6 ,")
/var/log/auth.log:Mar 14 10:23:33 myown-Desktop dbus[714]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.79" (uid=0 pid=3010 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=772 comm="NetworkManager ")
/var/log/auth.log:Mar 14 10:32:24 myown-Desktop dbus[714]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.79" (uid=0 pid=3010 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=772 comm="NetworkManager ")
/var/log/auth.log:Mar 14 10:32:25 myown-Desktop dbus[714]: [system] Rejected send message, 2 matched rules; type="error", sender=":1.5" (uid=0 pid=772 comm="NetworkManager ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.142" (uid=0 pid=4739 comm="/usr/sbin/pppd nodetach lock nodefaultroute ipv6 ,")
/var/log/auth.log:Mar 14 12:22:55 myown-Desktop dbus[686]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.80" (uid=0 pid=3148 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=744 comm="NetworkManager ")
/var/log/auth.log:Mar 14 13:11:35 myown-Desktop gnome-keyring-daemon[2353]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
/var/log/auth.log:Mar 14 13:11:35 myown-Desktop dbus[686]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.80" (uid=0 pid=3148 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=744 comm="NetworkManager ")
/var/log/auth.log:Mar 14 13:27:25 myown-Desktop dbus[709]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.81" (uid=0 pid=3263 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.3" (uid=0 pid=755 comm="NetworkManager ")
/var/log/auth.log:Mar 14 16:38:14 myown-Desktop sudo:  myown : TTY=pts/2 ; PWD=/home/myown ; USER=root ; COMMAND=/bin/egrep -i error|warning /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/pm-powersave.log /var/log/pm-suspend.log /var/log/prime-offload.log /var/log/prime-supported.log /var/log/syslog /var/log/Xorg.0.log /var/log/Xorg.1.log /var/log/Xorg.2.log /var/log/Xorg.failsafe.log
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 56 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 56 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 56 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: error: --compare-versions takes three arguments: <version> <relation> <version>
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:Preparing to unpack .../libgpg-error0_1.12-0.2ubuntu1_amd64.deb ...
/var/log/bootstrap.log:Unpacking libgpg-error0:amd64 (1.12-0.2ubuntu1) ...
/var/log/bootstrap.log:Setting up libgpg-error0:amd64 (1.12-0.2ubuntu1) ...
/var/log/dpkg.log:2015-03-13 16:37:31 status installed libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:38:07 status installed libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:38:13 status installed libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:38:18 status installed libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:38:24 status installed libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:38:29 status installed libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:38:35 status installed libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:38:40 status installed libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:38:46 status installed libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:39:05 status installed libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:39:05 remove libgpg-error0:i386 1.12-0.2ubuntu1 <none>
/var/log/dpkg.log:2015-03-13 16:39:05 status half-configured libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:39:05 status half-installed libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:39:05 status config-files libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:39:06 status config-files libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:46:50 install libgpg-error0:i386 1.12-0.2ubuntu1 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:46:50 status half-installed libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:46:50 status unpacked libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:46:50 status unpacked libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:49:10 configure libgpg-error0:i386 1.12-0.2ubuntu1 <none>
/var/log/dpkg.log:2015-03-13 16:49:10 status unpacked libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:49:10 status half-configured libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2015-03-13 16:49:10 status installed libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/kern.log:Mar 10 11:22:22 myown-Desktop kernel: [    0.578177] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 10 11:22:22 myown-Desktop kernel: [   25.005320] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 10 11:22:22 myown-Desktop kernel: [   25.005446] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 10 11:22:22 myown-Desktop kernel: [   25.005613] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 10 11:22:22 myown-Desktop kernel: [   27.503174] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 10 11:22:22 myown-Desktop kernel: [   27.503187] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 10 11:22:22 myown-Desktop kernel: [   27.503193] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 10 11:22:22 myown-Desktop kernel: [   27.503200] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 10 11:22:22 myown-Desktop kernel: [   27.503204] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 10 11:22:22 myown-Desktop kernel: [   28.166100] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 10 11:22:26 myown-Desktop kernel: [   32.852588] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 10 11:22:26 myown-Desktop kernel: [   32.852691] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 10 11:22:35 myown-Desktop kernel: [   44.829147] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 10 11:22:35 myown-Desktop kernel: [   44.829250] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 10 11:46:57 myown-Desktop kernel: [ 1508.419106] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 10 11:46:57 myown-Desktop kernel: [ 1508.419346] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 10 11:52:00 myown-Desktop kernel: [    0.161536] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 10 11:52:00 myown-Desktop kernel: [   16.874794] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 10 11:52:00 myown-Desktop kernel: [   16.874809] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 10 11:52:00 myown-Desktop kernel: [   16.874815] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 10 11:52:00 myown-Desktop kernel: [   16.874822] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 10 11:52:00 myown-Desktop kernel: [   16.874827] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 10 11:52:00 myown-Desktop kernel: [   16.890987] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 10 11:52:00 myown-Desktop kernel: [   16.891105] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 10 11:52:00 myown-Desktop kernel: [   16.891261] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 10 11:52:00 myown-Desktop kernel: [   20.581313] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 10 11:52:03 myown-Desktop kernel: [   24.826008] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 10 11:52:03 myown-Desktop kernel: [   24.826123] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 10 11:52:15 myown-Desktop kernel: [   36.934922] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 10 11:52:15 myown-Desktop kernel: [   36.935029] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 13:48:07 myown-Desktop kernel: [    0.577653] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 11 13:48:07 myown-Desktop kernel: [   19.495986] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 11 13:48:07 myown-Desktop kernel: [   19.495998] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 11 13:48:07 myown-Desktop kernel: [   19.496002] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 11 13:48:07 myown-Desktop kernel: [   19.496009] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 11 13:48:07 myown-Desktop kernel: [   19.496013] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 11 13:48:07 myown-Desktop kernel: [   19.561632] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 13:48:07 myown-Desktop kernel: [   19.561729] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 13:48:07 myown-Desktop kernel: [   19.561859] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 13:48:07 myown-Desktop kernel: [   22.281450] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 11 13:48:10 myown-Desktop kernel: [   25.776751] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 13:48:10 myown-Desktop kernel: [   25.776847] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 13:48:22 myown-Desktop kernel: [   37.771498] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 13:48:22 myown-Desktop kernel: [   37.771658] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 13:56:27 myown-Desktop kernel: [    0.577627] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 11 13:56:27 myown-Desktop kernel: [   17.534700] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 13:56:27 myown-Desktop kernel: [   17.534827] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 13:56:27 myown-Desktop kernel: [   17.534953] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 13:56:27 myown-Desktop kernel: [   18.664211] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 11 13:56:27 myown-Desktop kernel: [   18.664224] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 11 13:56:27 myown-Desktop kernel: [   18.664229] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 11 13:56:27 myown-Desktop kernel: [   18.664235] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 11 13:56:27 myown-Desktop kernel: [   18.664239] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 11 13:56:27 myown-Desktop kernel: [   20.722268] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 11 13:56:31 myown-Desktop kernel: [   24.822494] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 13:56:31 myown-Desktop kernel: [   24.822594] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 13:56:43 myown-Desktop kernel: [   36.963073] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 13:56:43 myown-Desktop kernel: [   36.963218] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 22:16:47 myown-Desktop kernel: [    0.576343] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 11 22:16:47 myown-Desktop kernel: [   25.013257] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 11 22:16:47 myown-Desktop kernel: [   25.013272] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 11 22:16:47 myown-Desktop kernel: [   25.013278] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 11 22:16:47 myown-Desktop kernel: [   25.013284] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 11 22:16:47 myown-Desktop kernel: [   25.013289] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 11 22:16:47 myown-Desktop kernel: [   25.053599] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 22:16:47 myown-Desktop kernel: [   25.053764] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 22:16:47 myown-Desktop kernel: [   25.053918] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 22:16:47 myown-Desktop kernel: [   32.102518] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 11 22:16:47 myown-Desktop kernel: [   32.757087] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 22:16:47 myown-Desktop kernel: [   32.757187] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 22:17:01 myown-Desktop kernel: [   47.764601] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 11 22:17:01 myown-Desktop kernel: [   47.764746] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 16:01:05 myown-Desktop kernel: [    0.577966] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 12 16:01:05 myown-Desktop kernel: [   19.928527] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 16:01:05 myown-Desktop kernel: [   19.928638] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 16:01:05 myown-Desktop kernel: [   19.928794] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 16:01:05 myown-Desktop kernel: [   21.122476] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 16:01:05 myown-Desktop kernel: [   21.122489] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 16:01:05 myown-Desktop kernel: [   21.122494] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 16:01:05 myown-Desktop kernel: [   21.122501] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 16:01:05 myown-Desktop kernel: [   21.122505] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 16:01:05 myown-Desktop kernel: [   24.064567] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 12 16:01:08 myown-Desktop kernel: [   27.831880] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 16:01:08 myown-Desktop kernel: [   27.832000] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 16:01:21 myown-Desktop kernel: [   40.817427] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 16:01:21 myown-Desktop kernel: [   40.817530] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 16:10:44 myown-Desktop kernel: [  606.544672] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 16:10:44 myown-Desktop kernel: [  606.544924] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 16:11:18 myown-Desktop kernel: [  641.465135] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 16:11:18 myown-Desktop kernel: [  641.465404] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 17:03:15 myown-Desktop kernel: [ 3761.589997] option1 ttyUSB0: option_instat_callback: error -71
/var/log/kern.log:Mar 12 20:42:11 myown-Desktop kernel: [    0.576437] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 12 20:42:11 myown-Desktop kernel: [   18.508899] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 20:42:11 myown-Desktop kernel: [   18.508911] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 20:42:11 myown-Desktop kernel: [   18.508915] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 20:42:11 myown-Desktop kernel: [   18.508920] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 20:42:11 myown-Desktop kernel: [   18.508923] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 20:42:11 myown-Desktop kernel: [   18.542310] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 20:42:11 myown-Desktop kernel: [   18.542410] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 20:42:11 myown-Desktop kernel: [   18.542543] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 20:42:11 myown-Desktop kernel: [   22.854493] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 12 20:42:13 myown-Desktop kernel: [   25.828096] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 20:42:13 myown-Desktop kernel: [   25.828220] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 20:42:26 myown-Desktop kernel: [   38.769869] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 20:42:26 myown-Desktop kernel: [   38.770012] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:10:37 myown-Desktop kernel: [    0.578305] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 12 21:10:37 myown-Desktop kernel: [   17.677877] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:10:37 myown-Desktop kernel: [   17.677954] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:10:37 myown-Desktop kernel: [   17.678046] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:10:37 myown-Desktop kernel: [   18.915137] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 21:10:37 myown-Desktop kernel: [   18.915230] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 21:10:37 myown-Desktop kernel: [   18.915237] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 21:10:37 myown-Desktop kernel: [   18.915245] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 21:10:37 myown-Desktop kernel: [   18.915249] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 21:10:37 myown-Desktop kernel: [   22.013363] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 12 21:10:39 myown-Desktop kernel: [   24.983302] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:10:39 myown-Desktop kernel: [   24.983401] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:10:53 myown-Desktop kernel: [   38.817666] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:10:53 myown-Desktop kernel: [   38.817765] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:37:25 myown-Desktop kernel: [    0.577437] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 12 21:37:25 myown-Desktop kernel: [   10.877558] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 12 21:37:25 myown-Desktop kernel: [   11.952695] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 21:37:25 myown-Desktop kernel: [   11.952710] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 21:37:25 myown-Desktop kernel: [   11.952716] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 21:37:25 myown-Desktop kernel: [   11.952723] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 21:37:25 myown-Desktop kernel: [   11.952728] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 12 21:38:10 myown-Desktop kernel: [   61.680818] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:38:14 myown-Desktop kernel: [   66.589983] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:38:14 myown-Desktop kernel: [   66.590062] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:38:14 myown-Desktop kernel: [   66.590113] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:38:14 myown-Desktop kernel: [   66.590168] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:38:14 myown-Desktop kernel: [   66.590215] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:38:14 myown-Desktop kernel: [   66.590261] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:38:14 myown-Desktop kernel: [   66.590411] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:38:14 myown-Desktop kernel: [   66.590482] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 12 21:38:15 myown-Desktop kernel: [   67.224697] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:47:31 myown-Desktop kernel: [    0.577509] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 13 08:47:31 myown-Desktop kernel: [   31.021059] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 08:47:31 myown-Desktop kernel: [   31.021074] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 08:47:31 myown-Desktop kernel: [   31.021079] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 08:47:31 myown-Desktop kernel: [   31.021087] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 08:47:31 myown-Desktop kernel: [   31.021091] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 08:47:31 myown-Desktop kernel: [   35.483407] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 13 08:47:38 myown-Desktop kernel: [   43.716635] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:47:39 myown-Desktop kernel: [   44.953101] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:47:39 myown-Desktop kernel: [   44.953220] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:47:39 myown-Desktop kernel: [   44.953303] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:47:39 myown-Desktop kernel: [   44.953397] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:47:39 myown-Desktop kernel: [   44.953478] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:47:39 myown-Desktop kernel: [   44.953558] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:47:39 myown-Desktop kernel: [   44.953703] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:47:39 myown-Desktop kernel: [   44.953787] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:47:40 myown-Desktop kernel: [   45.631516] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:58:15 myown-Desktop kernel: [    0.578244] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 13 08:58:15 myown-Desktop kernel: [   21.704953] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:58:15 myown-Desktop kernel: [   21.705064] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:58:15 myown-Desktop kernel: [   21.705157] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:58:15 myown-Desktop kernel: [   22.159269] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 08:58:15 myown-Desktop kernel: [   22.159280] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 08:58:15 myown-Desktop kernel: [   22.159285] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 08:58:15 myown-Desktop kernel: [   22.159291] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 08:58:15 myown-Desktop kernel: [   22.159295] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 08:58:15 myown-Desktop kernel: [   23.766271] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 13 08:58:19 myown-Desktop kernel: [   28.862597] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:58:19 myown-Desktop kernel: [   28.862696] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:58:28 myown-Desktop kernel: [   37.831967] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 08:58:28 myown-Desktop kernel: [   37.832066] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 09:17:01 myown-Desktop kernel: [ 1152.317304] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 09:17:01 myown-Desktop kernel: [ 1152.317554] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 09:24:33 myown-Desktop kernel: [ 1596.446259] PM: Device 00:07 failed to resume: error -19
/var/log/kern.log:Mar 13 09:24:38 myown-Desktop kernel: [ 1604.024506] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 09:24:38 myown-Desktop kernel: [ 1604.024760] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 16:17:55 myown-Desktop kernel: [26427.239825] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 16:17:55 myown-Desktop kernel: [26427.239934] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 17:16:51 myown-Desktop kernel: [29967.569035] option1 ttyUSB0: option_instat_callback: error -71
/var/log/kern.log:Mar 13 17:31:20 myown-Desktop kernel: [    0.577815] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 13 17:31:20 myown-Desktop kernel: [   19.966172] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 17:31:20 myown-Desktop kernel: [   19.966188] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 17:31:20 myown-Desktop kernel: [   19.966193] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 17:31:20 myown-Desktop kernel: [   19.966201] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 17:31:20 myown-Desktop kernel: [   19.966205] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 17:31:20 myown-Desktop kernel: [   20.397512] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 17:31:20 myown-Desktop kernel: [   20.397622] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 17:31:20 myown-Desktop kernel: [   20.397772] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 17:31:20 myown-Desktop kernel: [   23.103317] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 13 17:31:24 myown-Desktop kernel: [   27.833656] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 17:31:24 myown-Desktop kernel: [   27.833803] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 17:31:34 myown-Desktop kernel: [   38.020289] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 17:31:34 myown-Desktop kernel: [   38.020392] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 18:02:32 myown-Desktop kernel: [ 1898.613559] gpartedbin[4408]: segfault at 22680f ip 00007fd4ca62af31 sp 00007fff2665a930 error 6 in libc-2.19.so[7fd4ca5ab000+1bb000]
/var/log/kern.log:Mar 13 18:29:57 myown-Desktop kernel: [    0.576208] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 13 18:29:57 myown-Desktop kernel: [   19.659301] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 18:29:57 myown-Desktop kernel: [   19.659317] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 18:29:57 myown-Desktop kernel: [   19.659322] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 18:29:57 myown-Desktop kernel: [   19.659329] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 18:29:57 myown-Desktop kernel: [   19.659334] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 18:29:57 myown-Desktop kernel: [   20.106066] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 18:29:57 myown-Desktop kernel: [   20.106168] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 18:29:57 myown-Desktop kernel: [   20.106307] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 18:29:57 myown-Desktop kernel: [   22.176239] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 13 18:30:02 myown-Desktop kernel: [   27.774154] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 18:30:02 myown-Desktop kernel: [   27.774292] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 18:30:11 myown-Desktop kernel: [   36.736313] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 18:30:11 myown-Desktop kernel: [   36.736410] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 18:31:59 myown-Desktop kernel: [  145.480782] option1 ttyUSB0: option_instat_callback: error -71
/var/log/kern.log:Mar 13 19:59:06 myown-Desktop kernel: [    0.578145] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 13 19:59:06 myown-Desktop kernel: [   19.704837] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 19:59:06 myown-Desktop kernel: [   19.704852] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 19:59:06 myown-Desktop kernel: [   19.704857] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 19:59:06 myown-Desktop kernel: [   19.704864] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 19:59:06 myown-Desktop kernel: [   19.704868] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 13 19:59:06 myown-Desktop kernel: [   20.165318] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 19:59:06 myown-Desktop kernel: [   20.165426] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 19:59:06 myown-Desktop kernel: [   20.165569] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 19:59:06 myown-Desktop kernel: [   22.818444] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 13 19:59:09 myown-Desktop kernel: [   27.037493] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 19:59:09 myown-Desktop kernel: [   27.037589] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 19:59:20 myown-Desktop kernel: [   37.864805] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 13 19:59:20 myown-Desktop kernel: [   37.864903] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 09:54:54 myown-Desktop kernel: [    0.578156] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 14 09:54:54 myown-Desktop kernel: [   22.730037] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 09:54:54 myown-Desktop kernel: [   22.730052] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 09:54:54 myown-Desktop kernel: [   22.730058] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 09:54:54 myown-Desktop kernel: [   22.730066] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 09:54:54 myown-Desktop kernel: [   22.730071] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 09:54:54 myown-Desktop kernel: [   23.138428] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 09:54:54 myown-Desktop kernel: [   23.138534] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 09:54:54 myown-Desktop kernel: [   23.138681] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 09:54:54 myown-Desktop kernel: [   25.349903] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 14 09:54:59 myown-Desktop kernel: [   30.862431] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 09:54:59 myown-Desktop kernel: [   30.862531] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 09:55:08 myown-Desktop kernel: [   39.859837] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 09:55:08 myown-Desktop kernel: [   39.859948] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 10:18:27 myown-Desktop kernel: [ 1443.573541] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 10:18:27 myown-Desktop kernel: [ 1443.573797] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 12:20:53 myown-Desktop kernel: [    0.577531] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 14 12:20:53 myown-Desktop kernel: [   28.480743] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 12:20:53 myown-Desktop kernel: [   28.480758] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 12:20:53 myown-Desktop kernel: [   28.480764] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 12:20:53 myown-Desktop kernel: [   28.480771] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 12:20:53 myown-Desktop kernel: [   28.480776] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 12:20:53 myown-Desktop kernel: [   29.001472] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 12:20:53 myown-Desktop kernel: [   29.001579] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 12:20:53 myown-Desktop kernel: [   29.001875] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 12:20:53 myown-Desktop kernel: [   31.115486] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 14 12:20:57 myown-Desktop kernel: [   35.845848] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 12:20:57 myown-Desktop kernel: [   35.845950] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 12:21:07 myown-Desktop kernel: [   45.828297] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 12:21:07 myown-Desktop kernel: [   45.828439] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 13:11:41 myown-Desktop kernel: [ 3083.372030] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 13:11:41 myown-Desktop kernel: [ 3083.372282] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 13:25:52 myown-Desktop kernel: [    0.576551] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 14 13:25:52 myown-Desktop kernel: [   24.407844] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 13:25:52 myown-Desktop kernel: [   24.407859] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 13:25:52 myown-Desktop kernel: [   24.407865] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 13:25:52 myown-Desktop kernel: [   24.407872] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 13:25:52 myown-Desktop kernel: [   24.407876] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 13:25:52 myown-Desktop kernel: [   24.803286] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 13:25:52 myown-Desktop kernel: [   24.803396] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 13:25:52 myown-Desktop kernel: [   24.803539] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 13:25:52 myown-Desktop kernel: [   26.200587] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 14 13:25:57 myown-Desktop kernel: [   31.918605] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 13:25:57 myown-Desktop kernel: [   31.918713] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 13:26:08 myown-Desktop kernel: [   42.766630] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 13:26:08 myown-Desktop kernel: [   42.766728] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 13:26:25 myown-Desktop kernel: [   59.937370] type=1400 audit(1426335985.310:73): apparmor="DENIED" operation="mount" info="failed mntpnt match" error=-13 profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/" pid=2383 comm="init" fstype="proc" srcname="proc" flags="rw"
/var/log/kern.log:Mar 14 13:26:25 myown-Desktop kernel: [   59.937405] type=1400 audit(1426335985.310:74): apparmor="DENIED" operation="mount" info="failed mntpnt match" error=-13 profile="/usr/lib/lightdm/lightdm-guest-session" name="/sys/" pid=2383 comm="init" fstype="sysfs" srcname="sysfs" flags="rw"
/var/log/kern.log:Mar 14 13:26:25 myown-Desktop kernel: [   60.128984] type=1400 audit(1426335985.502:79): apparmor="DENIED" operation="mount" info="failed mntpnt match" error=-13 profile="/usr/lib/lightdm/lightdm-guest-session" name="/run/user/117/gvfs/" pid=2549 comm="gvfsd-fuse" fstype="fuse.gvfsd-fuse" srcname="gvfsd-fuse" flags="rw, nosuid, nodev"
/var/log/kern.log:Mar 14 16:35:03 myown-Desktop kernel: [    0.578262] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/kern.log:Mar 14 16:35:03 myown-Desktop kernel: [   19.797191] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 16:35:03 myown-Desktop kernel: [   19.797208] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 16:35:03 myown-Desktop kernel: [   19.797212] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 16:35:03 myown-Desktop kernel: [   19.797220] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 16:35:03 myown-Desktop kernel: [   19.797225] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/kern.log:Mar 14 16:35:03 myown-Desktop kernel: [   20.287952] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 16:35:03 myown-Desktop kernel: [   20.288060] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 16:35:03 myown-Desktop kernel: [   20.288312] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 16:35:03 myown-Desktop kernel: [   22.302988] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 14 16:35:08 myown-Desktop kernel: [   27.833551] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 16:35:08 myown-Desktop kernel: [   27.833647] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 16:35:17 myown-Desktop kernel: [   37.047085] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/kern.log:Mar 14 16:35:17 myown-Desktop kernel: [   37.047180] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-suspend.log:Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/var/log/pm-suspend.log:Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/var/log/pm-suspend.log:Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/var/log/pm-suspend.log:Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/var/log/syslog:Mar 14 13:11:41 myown-Desktop kernel: [ 3083.372030] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/syslog:Mar 14 13:11:41 myown-Desktop kernel: [ 3083.372282] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/syslog:Mar 14 13:12:11 myown-Desktop kernel: [ 3113.457182] systemd-hostnamed[5150]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
/var/log/syslog:Mar 14 13:25:52 myown-Desktop kernel: [    0.576551] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/syslog:Mar 14 13:25:52 myown-Desktop kernel: [   24.407844] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/syslog:Mar 14 13:25:52 myown-Desktop kernel: [   24.407859] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/syslog:Mar 14 13:25:52 myown-Desktop kernel: [   24.407865] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/syslog:Mar 14 13:25:52 myown-Desktop kernel: [   24.407872] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/syslog:Mar 14 13:25:52 myown-Desktop kernel: [   24.407876] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/syslog:Mar 14 13:25:52 myown-Desktop kernel: [   24.803286] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/syslog:Mar 14 13:25:52 myown-Desktop kernel: [   24.803396] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/syslog:Mar 14 13:25:52 myown-Desktop kernel: [   24.803539] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/syslog:Mar 14 13:25:52 myown-Desktop kernel: [   26.200587] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Mar 14 13:25:57 myown-Desktop kernel: [   31.918605] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/syslog:Mar 14 13:25:57 myown-Desktop kernel: [   31.918713] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/syslog:Mar 14 13:26:08 myown-Desktop kernel: [   42.766630] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/syslog:Mar 14 13:26:08 myown-Desktop kernel: [   42.766728] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/syslog:Mar 14 13:26:25 myown-Desktop kernel: [   59.937370] type=1400 audit(1426335985.310:73): apparmor="DENIED" operation="mount" info="failed mntpnt match" error=-13 profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/" pid=2383 comm="init" fstype="proc" srcname="proc" flags="rw"
/var/log/syslog:Mar 14 13:26:25 myown-Desktop kernel: [   59.937405] type=1400 audit(1426335985.310:74): apparmor="DENIED" operation="mount" info="failed mntpnt match" error=-13 profile="/usr/lib/lightdm/lightdm-guest-session" name="/sys/" pid=2383 comm="init" fstype="sysfs" srcname="sysfs" flags="rw"
/var/log/syslog:Mar 14 13:26:25 myown-Desktop kernel: [   60.128984] type=1400 audit(1426335985.502:79): apparmor="DENIED" operation="mount" info="failed mntpnt match" error=-13 profile="/usr/lib/lightdm/lightdm-guest-session" name="/run/user/117/gvfs/" pid=2549 comm="gvfsd-fuse" fstype="fuse.gvfsd-fuse" srcname="gvfsd-fuse" flags="rw, nosuid, nodev"
/var/log/syslog:Mar 14 13:26:29 myown-Desktop gnome-session[2656]: WARNING: Could not get session id for session. Check that logind is properly installed and pam_systemd is getting used at login.
/var/log/syslog:Mar 14 13:27:25 myown-Desktop NetworkManager[755]: <error> [1426336045.165356] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog:Mar 14 13:27:25 myown-Desktop dnsmasq[3263]: warning: no upstream servers configured
/var/log/syslog:Mar 14 13:28:03 myown-Desktop kernel: [  157.834748] systemd-hostnamed[3431]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
/var/log/syslog:Mar 14 16:35:03 myown-Desktop kernel: [    0.578262] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
/var/log/syslog:Mar 14 16:35:03 myown-Desktop kernel: [   19.797191] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
/var/log/syslog:Mar 14 16:35:03 myown-Desktop kernel: [   19.797208] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/syslog:Mar 14 16:35:03 myown-Desktop kernel: [   19.797212] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/syslog:Mar 14 16:35:03 myown-Desktop kernel: [   19.797220] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
/var/log/syslog:Mar 14 16:35:03 myown-Desktop kernel: [   19.797225] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
/var/log/syslog:Mar 14 16:35:03 myown-Desktop kernel: [   20.287952] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/syslog:Mar 14 16:35:03 myown-Desktop kernel: [   20.288060] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/syslog:Mar 14 16:35:03 myown-Desktop kernel: [   20.288312] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/syslog:Mar 14 16:35:03 myown-Desktop kernel: [   22.302988] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Mar 14 16:35:08 myown-Desktop kernel: [   27.833551] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/syslog:Mar 14 16:35:08 myown-Desktop kernel: [   27.833647] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/syslog:Mar 14 16:35:17 myown-Desktop kernel: [   37.047085] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/syslog:Mar 14 16:35:17 myown-Desktop kernel: [   37.047180] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
/var/log/Xorg.0.log:	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.0.log:[    31.419] (WW) Warning, couldn't open module nvidia
/var/log/Xorg.0.log:[    31.611] (WW) Warning, couldn't open module nvidia
/var/log/Xorg.1.log:	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.1.log:[  6399.379] (WW) Warning, couldn't open module nvidia
/var/log/Xorg.1.log:[  6399.381] (WW) Warning, couldn't open module nvidia
/var/log/Xorg.2.log:	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.2.log:[ 27781.776] (WW) Warning, couldn't open module nvidia
/var/log/Xorg.2.log:[ 27781.871] (WW) Warning, couldn't open module nvidia
/var/log/Xorg.2.log:[ 27791.859] Error dropping master: -22(Invalid argument)
/var/log/Xorg.failsafe.log:	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
```

NB: I am no expert on these things, just picked up the command by chance.

Thanks,

siggi

---

### Post by TheFu on 2015-03-14
Don't worry about bootstrap.log - that is from the installation when the installer was trying to figure out what your system is, has, and what it should use. Mind hasn't been modified since the install date last summer.

You need to pick one issue at a time and work it.  Seems there are many package management issues. Having mixed packages can cause all sorts of bad things.
To start:
**sudo apt-get update && sudo apt-get dist-upgrade**
Post any errors.

The main errors/warnings to be concerned about will be in dmesg or syslog or auth.log.

BTW, that looks like a command from my blog.  There shouldn't be any errors in current log files. Some errors matter less than others. For example, DVD read/buffer errors probably don't matter and tainted kernel no DRM errors don't matter either.  OTOH, errors with access to disk partitions - THAT is important to solve - don't want data corruption, right?

---

### Post by siggi2 on 2015-03-15
> **TheFu said:**
> ... OTOH, errors with access to disk partitions - THAT is important to solve - don't want data corruption, right?

Thanks, and where do I find these partition errors in my output, please?

By the way, *sudo apt-get update && sudo apt-get dist-upgrade* did not produce any errors.

> ...BTW, that looks like a command from my blog...
Very possible, but I do not remember where I found it.

---

### Post by TheFu on 2015-03-15
> **siggi2 said:**
> Thanks, and where do I find these partition errors in my output, please?

By the way, *sudo apt-get update && sudo apt-get dist-upgrade* did not produce any errors. 

You need to review the log files and any important errors. Google the exact error, leaving out any machine specific things like timestamps, hostnames, etc.  In time, that knowledge will build and you'll get to know what is and is not important. In the beginning, it takes time.

At least the box it patched. That was my initial worry.  I would look into the I/O errors - the lines nearby should help determine what those are about. Could be anything from a failed disk (important!) to an external server that hasn't existing in years, but Ubuntu still wants to connect to get ads(completely unimportant).

---

