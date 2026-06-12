---
title: "Session keeps ending in Ubuntu 12.10"
date: 2013-01-09
forum: Desktop Environments
---

### Post by nmr on 2013-01-09
Hello,

I have:
12.04 (precise) 32-bit distribution
Kernel Linux 3.2.0-35-generic-pae
GNOME 3.4.2 with Desktop Unity 3D

and use no NVIDIA or other proprietary Graphic Card drivers. 

For the last weeks, my session ends abruptly, aparently for no reason, while I'm working. It's hard to make sense of it, and it happens quite often, lately several times a day. Yesterday it happened when I was using the native photo visualization tool. But usually it happens when I am online, using Firefox or Chrome or using LibreOffice. Or maybe some other application. And it happens both when I have severall applications opened and when I only am using one. and, as far as I could tell, it happens both when I use online and offline aplications. Like I said it's quite hard for me to make sense of it, and Apport, when I log back, does not get triggered.

This is my auth.log, and it has the info on the last few times the session closed, including one just a few minutes ago:

```
Jan  8 00:17:01 nuno-System-Name CRON[2897]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  8 00:17:01 nuno-System-Name CRON[2897]: pam_unix(cron:session): session closed for user root
Jan  8 00:20:45 nuno-System-Name polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.53, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale pt_PT.UTF-8) (disconnected from bus)
Jan  8 12:27:31 nuno-System-Name lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Jan  8 12:27:31 nuno-System-Name lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jan  8 12:27:35 nuno-System-Name lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "nuno"
Jan  8 12:27:35 nuno-System-Name dbus[490]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.26" (uid=104 pid=1471 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1192 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 12:27:49 nuno-System-Name lightdm: pam_unix(lightdm:session): session closed for user lightdm
Jan  8 12:27:49 nuno-System-Name lightdm: pam_unix(lightdm:session): session opened for user nuno by (uid=0)
Jan  8 12:27:49 nuno-System-Name lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jan  8 12:27:56 nuno-System-Name polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.51 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale pt_PT.UTF-8)
Jan  8 12:28:25 nuno-System-Name dbus[490]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.61" (uid=1000 pid=1957 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1192 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 12:28:30 nuno-System-Name dbus[490]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.64" (uid=1000 pid=2028 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1192 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 13:17:02 nuno-System-Name CRON[2684]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  8 13:17:02 nuno-System-Name CRON[2684]: pam_unix(cron:session): session closed for user root
Jan  8 13:26:20 nuno-System-Name polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.51, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale pt_PT.UTF-8) (disconnected from bus)
Jan  8 13:26:21 nuno-System-Name lightdm: pam_unix(lightdm:session): session closed for user nuno
Jan  8 13:26:24 nuno-System-Name lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Jan  8 13:26:24 nuno-System-Name lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :1
Jan  8 13:26:28 nuno-System-Name lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "nuno"
Jan  8 13:26:29 nuno-System-Name dbus[490]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.81" (uid=104 pid=2908 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1192 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 13:26:30 nuno-System-Name dbus[490]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.90" (uid=104 pid=2950 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1192 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 13:26:35 nuno-System-Name lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:1 ruser= rhost=  user=nuno
Jan  8 13:26:35 nuno-System-Name lightdm: pam_winbind(lightdm:auth): getting password (0x00000388)
Jan  8 13:26:35 nuno-System-Name lightdm: pam_winbind(lightdm:auth): pam_get_item returned a password
Jan  8 13:26:35 nuno-System-Name lightdm: pam_winbind(lightdm:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  8 13:26:38 nuno-System-Name lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "nuno"
Jan  8 13:26:49 nuno-System-Name lightdm: pam_unix(lightdm:session): session closed for user lightdm
Jan  8 13:26:50 nuno-System-Name lightdm: pam_unix(lightdm:session): session opened for user nuno by (uid=0)
Jan  8 13:26:50 nuno-System-Name lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :1
Jan  8 13:26:55 nuno-System-Name polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session4 (system bus name :1.101 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale pt_PT.UTF-8)
Jan  8 13:27:08 nuno-System-Name dbus[490]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.109" (uid=1000 pid=3267 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1192 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 13:27:13 nuno-System-Name dbus[490]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.113" (uid=1000 pid=3360 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1192 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 13:27:17 nuno-System-Name dbus[490]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.119" (uid=1000 pid=3424 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1192 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 13:27:21 nuno-System-Name dbus[490]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=3470 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1192 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 13:27:24 nuno-System-Name dbus[490]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.126" (uid=1000 pid=3513 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1192 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 13:31:14 nuno-System-Name dbus[490]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.137" (uid=1000 pid=3727 comm="/usr/bin/python /usr/share/apport/apport-gtk ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1192 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 13:31:14 nuno-System-Name dbus[490]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.137" (uid=1000 pid=3727 comm="/usr/bin/python /usr/share/apport/apport-gtk ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1192 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 13:56:30 nuno-System-Name polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session4 (system bus name :1.101, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale pt_PT.UTF-8) (disconnected from bus)
Jan  8 13:56:31 nuno-System-Name lightdm: pam_unix(lightdm:session): session closed for user nuno
Jan  8 13:56:33 nuno-System-Name lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Jan  8 13:56:33 nuno-System-Name lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :2
Jan  8 13:56:36 nuno-System-Name lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "nuno"
Jan  8 13:56:37 nuno-System-Name dbus[490]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.144" (uid=104 pid=8280 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1192 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 13:56:38 nuno-System-Name dbus[490]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.153" (uid=104 pid=8321 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1192 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 13:56:45 nuno-System-Name lightdm: pam_unix(lightdm:session): session closed for user lightdm
Jan  8 13:56:46 nuno-System-Name lightdm: pam_unix(lightdm:session): session opened for user nuno by (uid=0)
Jan  8 13:56:46 nuno-System-Name lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :2
Jan  8 13:56:51 nuno-System-Name polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session6 (system bus name :1.163 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale pt_PT.UTF-8)
Jan  8 13:57:04 nuno-System-Name dbus[490]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.172" (uid=1000 pid=8637 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1192 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 14:17:01 nuno-System-Name CRON[9086]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  8 14:17:01 nuno-System-Name CRON[9086]: pam_unix(cron:session): session closed for user root
Jan  8 14:40:43 nuno-System-Name polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session6 (system bus name :1.163, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale pt_PT.UTF-8) (disconnected from bus)
Jan  8 14:40:59 nuno-System-Name lightdm: pam_unix(lightdm:session): session closed for user nuno
Jan  8 14:41:00 nuno-System-Name lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Jan  8 14:41:00 nuno-System-Name lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :2
Jan  8 14:41:03 nuno-System-Name lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "nuno"
Jan  8 14:41:04 nuno-System-Name dbus[490]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.195" (uid=104 pid=9308 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1192 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 14:42:55 nuno-System-Name lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "nuno"
Jan  8 14:44:00 nuno-System-Name lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Jan  8 14:44:00 nuno-System-Name lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jan  8 14:44:06 nuno-System-Name lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "nuno"
Jan  8 14:44:08 nuno-System-Name dbus[689]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.25" (uid=104 pid=1433 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1300 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 14:44:11 nuno-System-Name dbus[689]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.33" (uid=104 pid=1585 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1300 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 14:47:28 nuno-System-Name lightdm: pam_unix(lightdm:session): session closed for user lightdm
Jan  8 14:47:29 nuno-System-Name lightdm: pam_unix(lightdm:session): session opened for user nuno by (uid=0)
Jan  8 14:47:29 nuno-System-Name lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jan  8 14:47:37 nuno-System-Name polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.49 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale pt_PT.UTF-8)
Jan  8 14:48:05 nuno-System-Name dbus[689]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.60" (uid=1000 pid=1964 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1300 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 14:48:10 nuno-System-Name dbus[689]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.65" (uid=1000 pid=2034 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1300 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 14:48:13 nuno-System-Name dbus[689]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.67" (uid=1000 pid=2086 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1300 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  8 15:17:01 nuno-System-Name CRON[2307]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  8 15:17:01 nuno-System-Name CRON[2307]: pam_unix(cron:session): session closed for user root
Jan  8 16:17:01 nuno-System-Name CRON[2329]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  8 16:17:01 nuno-System-Name CRON[2329]: pam_unix(cron:session): session closed for user root
Jan  8 17:17:01 nuno-System-Name CRON[2516]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  8 17:17:01 nuno-System-Name CRON[2516]: pam_unix(cron:session): session closed for user root
Jan  8 18:17:01 nuno-System-Name CRON[2745]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  8 18:17:01 nuno-System-Name CRON[2745]: pam_unix(cron:session): session closed for user root
Jan  8 19:17:01 nuno-System-Name CRON[2960]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  8 19:17:01 nuno-System-Name CRON[2960]: pam_unix(cron:session): session closed for user root
Jan  8 20:17:01 nuno-System-Name CRON[3238]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  8 20:17:01 nuno-System-Name CRON[3238]: pam_unix(cron:session): session closed for user root
Jan  8 21:17:02 nuno-System-Name CRON[3669]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  8 21:17:02 nuno-System-Name CRON[3669]: pam_unix(cron:session): session closed for user root
Jan  8 22:17:01 nuno-System-Name CRON[4077]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  8 22:17:01 nuno-System-Name CRON[4077]: pam_unix(cron:session): session closed for user root
Jan  8 23:17:01 nuno-System-Name CRON[4485]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  8 23:17:01 nuno-System-Name CRON[4485]: pam_unix(cron:session): session closed for user root
Jan  9 00:17:02 nuno-System-Name CRON[4901]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 00:17:02 nuno-System-Name CRON[4901]: pam_unix(cron:session): session closed for user root
Jan  9 01:17:01 nuno-System-Name CRON[5309]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 01:17:01 nuno-System-Name CRON[5309]: pam_unix(cron:session): session closed for user root
Jan  9 02:08:22 nuno-System-Name gnome-keyring-daemon[1638]: couldn't allocate secure memory to keep passwords and or keys from being written to the disk
Jan  9 02:17:01 nuno-System-Name CRON[6382]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 02:17:01 nuno-System-Name CRON[6382]: pam_unix(cron:session): session closed for user root
Jan  9 02:17:53 nuno-System-Name polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.49, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale pt_PT.UTF-8) (disconnected from bus)
Jan  9 02:18:11 nuno-System-Name lightdm: pam_unix(lightdm:session): session closed for user nuno
Jan  9 02:18:13 nuno-System-Name lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Jan  9 02:18:13 nuno-System-Name lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jan  9 02:18:15 nuno-System-Name lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "nuno"
Jan  9 02:18:16 nuno-System-Name dbus[689]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.116" (uid=104 pid=6487 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1300 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  9 02:18:26 nuno-System-Name lightdm: pam_unix(lightdm:session): session closed for user lightdm
Jan  9 02:18:26 nuno-System-Name lightdm: pam_unix(lightdm:session): session opened for user nuno by (uid=0)
Jan  9 02:18:26 nuno-System-Name lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jan  9 02:18:32 nuno-System-Name polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session4 (system bus name :1.131 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale pt_PT.UTF-8)
Jan  9 02:18:45 nuno-System-Name dbus[689]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.138" (uid=1000 pid=6819 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1300 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  9 02:33:14 nuno-System-Name sudo: pam_unix(sudo:auth): authentication failure; logname=nuno uid=1000 euid=0 tty=/dev/pts/0 ruser=nuno rhost=  user=nuno
Jan  9 02:33:40 nuno-System-Name sudo:     nuno : TTY=pts/0 ; PWD=/home/nuno ; USER=root ; COMMAND=/usr/bin/apt-get update
Jan  9 02:33:40 nuno-System-Name sudo: pam_unix(sudo:session): session opened for user root by nuno(uid=1000)
Jan  9 02:34:02 nuno-System-Name sudo: pam_unix(sudo:session): session closed for user root
Jan  9 02:34:43 nuno-System-Name sudo:     nuno : TTY=pts/0 ; PWD=/home/nuno ; USER=root ; COMMAND=/usr/bin/apt-get upgrade
Jan  9 02:34:43 nuno-System-Name sudo: pam_unix(sudo:session): session opened for user root by nuno(uid=1000)
Jan  9 02:35:29 nuno-System-Name sudo: pam_unix(sudo:session): session closed for user root
Jan  9 02:36:19 nuno-System-Name sudo:     nuno : TTY=pts/0 ; PWD=/home/nuno ; USER=root ; COMMAND=/usr/bin/apt-get install wine
Jan  9 02:36:19 nuno-System-Name sudo: pam_unix(sudo:session): session opened for user root by nuno(uid=1000)
Jan  9 02:36:21 nuno-System-Name sudo: pam_unix(sudo:session): session closed for user root
Jan  9 02:58:08 nuno-System-Name polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session4 (system bus name :1.131, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale pt_PT.UTF-8) (disconnected from bus)
Jan  9 14:25:15 nuno-System-Name lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Jan  9 14:25:15 nuno-System-Name lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jan  9 14:25:18 nuno-System-Name lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "nuno"
Jan  9 14:25:19 nuno-System-Name dbus[440]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.25" (uid=104 pid=1489 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1199 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  9 14:25:38 nuno-System-Name lightdm: pam_unix(lightdm:session): session closed for user lightdm
Jan  9 14:25:38 nuno-System-Name lightdm: pam_unix(lightdm:session): session opened for user nuno by (uid=0)
Jan  9 14:25:38 nuno-System-Name lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jan  9 14:25:45 nuno-System-Name polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.51 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale pt_PT.UTF-8)
Jan  9 14:26:10 nuno-System-Name dbus[440]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.60" (uid=1000 pid=1944 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1199 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  9 15:17:01 nuno-System-Name CRON[2627]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 15:17:01 nuno-System-Name CRON[2627]: pam_unix(cron:session): session closed for user root
Jan  9 16:17:01 nuno-System-Name CRON[2661]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 16:17:01 nuno-System-Name CRON[2661]: pam_unix(cron:session): session closed for user root
Jan  9 17:17:01 nuno-System-Name CRON[2696]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 17:17:01 nuno-System-Name CRON[2696]: pam_unix(cron:session): session closed for user root
Jan  9 18:17:01 nuno-System-Name CRON[2732]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 18:17:01 nuno-System-Name CRON[2732]: pam_unix(cron:session): session closed for user root
Jan  9 19:17:01 nuno-System-Name CRON[2767]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 19:17:01 nuno-System-Name CRON[2767]: pam_unix(cron:session): session closed for user root
Jan  9 20:08:53 nuno-System-Name polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.51, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale pt_PT.UTF-8) (disconnected from bus)
Jan  9 20:08:55 nuno-System-Name lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Jan  9 20:08:55 nuno-System-Name lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :1
Jan  9 20:08:58 nuno-System-Name lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "nuno"
Jan  9 20:08:58 nuno-System-Name dbus[440]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.99" (uid=104 pid=3621 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1199 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  9 20:09:06 nuno-System-Name lightdm: pam_unix(lightdm:session): session closed for user lightdm
Jan  9 20:09:06 nuno-System-Name lightdm: pam_unix(lightdm:session): session opened for user nuno by (uid=0)
Jan  9 20:09:06 nuno-System-Name lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :1
Jan  9 20:09:10 nuno-System-Name polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session4 (system bus name :1.117 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale pt_PT.UTF-8)
Jan  9 20:09:23 nuno-System-Name dbus[440]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.125" (uid=1000 pid=3957 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1199 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  9 20:14:52 nuno-System-Name sudo:     nuno : TTY=pts/0 ; PWD=/home/nuno ; USER=root ; COMMAND=/usr/bin/nautilus
Jan  9 20:14:52 nuno-System-Name sudo: pam_unix(sudo:session): session opened for user root by nuno(uid=1000)
Jan  9 20:17:01 nuno-System-Name CRON[4598]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 20:17:01 nuno-System-Name CRON[4598]: pam_unix(cron:session): session closed for user root
```This is becoming disruptive and I've lost work already. I've searched online on the usual sources about this but mostly found users that had this problem with older versions of Ubuntu. And the help provided usually indicated that they had a specific problem in their instalation. So I could not extract any generic help from their cases.

If anyone has any advice, I would be extremely grateful. I am not very code savvy but I try to learn what I can from those who are willing to help. Hope this log has any use, please let me know if there is any other info I should provide.

Thank you for your time,
Nuno.

---

### Post by Juniorr on 2013-01-09
I had this once. Installing the latest 310 Nvidia driver from Addicional Drivers solve my problem. Also, there's another way to fix this:

> sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade

Hope it helps

---

### Post by nmr on 2013-01-10
Juniorr,

I've updated the X.org repositories and updated, using the code you provided. Thank you. My graphic card is an NVIDIA, but for now I would prefer not to use their drivers. In the next few days I'll see if this fixes the problem, and if it does, I'll close the thread. If not, I'll try to use the NVIDIA drivers, using the info on the Linux NVIDIA Forums. But it's quite tricky, with a lot of things that need to be deleted or added from my system, files that need tweaking and things like that. Hope I don't need to use it [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490).

Thank you again for your help,
So far, it hasn't happened again,
hope it's fixed,
Nuno.

---

### Post by nmr on 2013-01-14
I'm marking this thread as solved.

For the last days, after using

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade 
```

the problem never happened again.
I'm assuming it is fixed, and that updating X.org solved it.

---

