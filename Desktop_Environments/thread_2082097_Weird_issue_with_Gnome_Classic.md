---
title: "Weird issue with Gnome Classic"
date: 2012-11-08
forum: Desktop Environments
---

### Post by Dural on 2012-11-08
I am running Ubuntu 12.04 LTS. About thirty minutes ago, my system froze except for my mouse. I had run into this issue in the past so I pressed alt+f2 to get to the recovery console. Then I did sudo services lightdm restart so I could get back to the login. Everything went back to normal and I got up for a few minutes to do something else. When I came back to my computer, I saw the message that pops up when you do something like shut down the computer (the whole sequence which shows an action and [OK] on the right side; not sure what it's called), but the computer did not turn off. I also saw my whole password displayed in plaintext. I tried running the sudo command to restart lightdm but it didn't work and I had no idea what to do so I just turned off my computer. Is this a bug in Ubuntu or a sign of an attempted attack? If so, I know I'm going to change my password but what else should I do?

---

### Post by dannyboy79 on 2012-11-08
where did you see your password entered in plaintext? do you have a NAT router you're behind or are you connected dirctly to the internet?

---

### Post by Dural on 2012-11-08
It was under all of the shutdown information but before I tried entering the sudo command. It was also placed in the middle of the screen. 

I am behind a NAT router and I also use a software firewall (GUFW). It wasn't the network password that was displayed; it was my user login.

---

### Post by dannyboy79 on 2012-11-08
take a look at your /var/log/auth.log file to see if theres anything weird. If you don't have any open ports in your router it's likely doubtful your computer was compromised. I am not sure whaere you saw your user's password on the screen in plaintext.

---

### Post by Dural on 2012-11-08
Would it be safe for me to put up some of the information that showed up in auth.log when the issue occurred? If so, I can add it to this post because I'm not really sure what's normal and what isn't from the file.

> Nov  8 08:13:05 maggiesimpson su[19770]: Successful su for maggiesimpson by root
Nov  8 08:13:05 maggiesimpson su[19770]: + ??? root:maggiesimpson
Nov  8 08:13:05 maggiesimpson su[19770]: pam_unix(su:session): session opened for user maggiesimpson by (uid=0)
Nov  8 08:13:05 maggiesimpson su[19770]: pam_unix(su:session): session closed for user maggiesimpson
Nov  8 08:13:05 maggiesimpson su[19782]: Successful su for maggiesimpson by root
Nov  8 08:13:05 maggiesimpson su[19782]: + ??? root:maggiesimpson
Nov  8 08:13:05 maggiesimpson su[19782]: pam_unix(su:session): session opened for user maggiesimpson by (uid=0)
Nov  8 08:13:06 maggiesimpson su[19782]: pam_unix(su:session): session closed for user maggiesimpson
Nov  8 08:13:06 maggiesimpson su[19795]: Successful su for maggiesimpson by root
Nov  8 08:13:06 maggiesimpson su[19795]: + ??? root:maggiesimpson
Nov  8 08:13:06 maggiesimpson su[19795]: pam_unix(su:session): session opened for user maggiesimpson by (uid=0)
Nov  8 08:13:06 maggiesimpson su[19795]: pam_unix(su:session): session closed for user maggiesimpson
Nov  8 08:13:06 maggiesimpson su[19812]: Successful su for maggiesimpson by root
Nov  8 08:13:06 maggiesimpson su[19812]: + ??? root:maggiesimpson
Nov  8 08:13:06 maggiesimpson su[19812]: pam_unix(su:session): session opened for user maggiesimpson by (uid=0)
Nov  8 08:13:06 maggiesimpson su[19812]: pam_unix(su:session): session closed for user maggiesimpson
Nov  8 08:13:06 maggiesimpson su[19827]: Successful su for maggiesimpson by root
Nov  8 08:13:06 maggiesimpson su[19827]: + ??? root:maggiesimpson
Nov  8 08:13:06 maggiesimpson su[19827]: pam_unix(su:session): session opened for user maggiesimpson by (uid=0)
Nov  8 08:13:06 maggiesimpson su[19827]: pam_unix(su:session): session closed for user maggiesimpson
Nov  8 08:13:06 maggiesimpson su[19840]: Successful su for maggiesimpson by root
Nov  8 08:13:06 maggiesimpson su[19840]: + ??? root:maggiesimpson
Nov  8 08:13:06 maggiesimpson su[19840]: pam_unix(su:session): session opened for user maggiesimpson by (uid=0)
Nov  8 08:13:06 maggiesimpson su[19840]: pam_unix(su:session): session closed for user maggiesimpson
Nov  8 08:13:09 maggiesimpson pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Nov  8 08:13:09 maggiesimpson pkexec: pam_ck_connector(polkit-1:session): cannot determine display-device
Nov  8 08:13:09 maggiesimpson pkexec[20014]: maggiesimpson: Executing command [USER=root] [TTY=unknown] [CWD=/home/maggiesimpson] [COMMAND=/usr/lib/gnome-settings-daemon/gsd-backlight-helper --set-brightness 2]
Nov  8 08:13:10 maggiesimpson pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Nov  8 08:13:10 maggiesimpson pkexec: pam_ck_connector(polkit-1:session): cannot determine display-device
Nov  8 08:13:10 maggiesimpson pkexec[20020]: maggiesimpson: Executing command [USER=root] [TTY=unknown] [CWD=/home/maggiesimpson] [COMMAND=/usr/lib/gnome-settings-daemon/gsd-backlight-helper --set-brightness 4]
Nov  8 08:13:11 maggiesimpson pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Nov  8 08:13:11 maggiesimpson pkexec: pam_ck_connector(polkit-1:session): cannot determine display-device
Nov  8 08:13:11 maggiesimpson pkexec[20026]: maggiesimpson: Executing command [USER=root] [TTY=unknown] [CWD=/home/maggiesimpson] [COMMAND=/usr/lib/gnome-settings-daemon/gsd-backlight-helper --set-brightness 6]
Nov  8 08:17:02 maggiesimpson CRON[20113]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  8 08:17:02 maggiesimpson CRON[20113]: pam_unix(cron:session): session closed for user root
Nov  8 08:51:50 maggiesimpson login[1084]: pam_unix(login:session): session opened for user maggiesimpson by LOGIN(uid=0)
Nov  8 08:55:04 maggiesimpson su[20835]: Successful su for maggiesimpson by root
Nov  8 08:55:04 maggiesimpson su[20835]: + ??? root:maggiesimpson
Nov  8 08:55:04 maggiesimpson su[20835]: pam_unix(su:session): session opened for user maggiesimpson by (uid=0)
Nov  8 08:55:04 maggiesimpson su[20835]: pam_unix(su:session): session closed for user maggiesimpson
Nov  8 08:55:17 maggiesimpson sudo: maggiesimpson : TTY=tty2 ; PWD=/home/maggiesimpson ; USER=root ; COMMAND=/usr/sbin/service lightdm restart
Nov  8 08:55:17 maggiesimpson sudo: pam_unix(sudo:session): session opened for user root by maggiesimpson(uid=1000)
Nov  8 08:55:18 maggiesimpson lightdm: pam_unix(lightdm:session): session closed for user maggiesimpson
Nov  8 08:55:19 maggiesimpson polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.45, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)
Nov  8 08:55:23 maggiesimpson sudo: pam_unix(sudo:session): session closed for user root
Nov  8 08:55:27 maggiesimpson lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Nov  8 08:55:27 maggiesimpson lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :1
Nov  8 08:55:31 maggiesimpson lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "maggiesimpson"
Nov  8 08:55:32 maggiesimpson dbus[894]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.578" (uid=104 pid=20957 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1367 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Nov  8 08:55:33 maggiesimpson dbus[894]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.586" (uid=104 pid=20999 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1367 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Nov  8 08:55:49 maggiesimpson lightdm: pam_unix(lightdm:session): session closed for user lightdm
Nov  8 08:55:49 maggiesimpson lightdm: pam_unix(lightdm:session): session opened for user maggiesimpson by (uid=0)
Nov  8 08:55:49 maggiesimpson lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :1
Nov  8 08:55:52 maggiesimpson polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session164 (system bus name :1.593 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Nov  8 08:55:56 maggiesimpson dbus[894]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.603" (uid=1000 pid=21209 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1367 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Nov  8 09:17:01 maggiesimpson CRON[22286]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  8 09:17:01 maggiesimpson CRON[22286]: pam_unix(cron:session): session closed for user root
Nov  8 09:22:21 maggiesimpson su[22342]: Successful su for maggiesimpson by root
Nov  8 09:22:21 maggiesimpson su[22342]: + ??? root:maggiesimpson
Nov  8 09:22:21 maggiesimpson su[22342]: pam_unix(su:session): session opened for user maggiesimpson by (uid=0)
Nov  8 09:22:22 maggiesimpson su[22342]: pam_unix(su:session): session closed for user maggiesimpson
Nov  8 09:25:30 maggiesimpson lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Nov  8 09:25:30 maggiesimpson lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Nov  8 09:25:37 maggiesimpson lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "maggiesimpson"
Nov  8 09:25:38 maggiesimpson dbus[805]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.24" (uid=104 pid=1673 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=1370 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Nov  8 09:25:41 maggiesimpson dbus[805]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.35" (uid=104 pid=1790 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=1370 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Nov  8 09:26:22 maggiesimpson lightdm: pam_unix(lightdm:session): session closed for user lightdm
Nov  8 09:26:22 maggiesimpson lightdm: pam_unix(lightdm:session): session opened for user maggiesimpson by (uid=0)
Nov  8 09:26:22 maggiesimpson lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Nov  8 09:26:26 maggiesimpson polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.48 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Nov  8 09:26:54 maggiesimpson dbus[805]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.62" (uid=1000 pid=2063 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=1370 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Nov  8 09:50:26 maggiesimpson gnome-keyring-daemon[1836]: unsupported key algorithm in certificate: 1.2.840.10045.2.1
Nov  8 09:51:19  gnome-keyring-daemon[1836]: last message repeated 9 times
Nov  8 09:51:59 maggiesimpson polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 successfully authenticated as unix-user:maggiesimpson to gain TEMPORARY authorization for action org.freedesktop.accounts.user-administration for unix-process:2445:159036 [gnome-control-center --overview] (owned by unix-user:maggiesimpson)
Nov  8 09:59:07 maggiesimpson passwd[2479]: pam_unix(passwd:chauthtok): password changed for maggiesimpson
Nov  8 09:59:07 maggiesimpson gnome-keyring-daemon[2488]: Gck: gck_module_new: assertion `funcs' failed
Nov  8 09:59:07 maggiesimpson gnome-keyring-daemon[2488]: module_instances: assertion `module' failed
Nov  8 09:59:07 maggiesimpson gnome-keyring-daemon[2488]: egg_error_message: assertion `error' failed
Nov  8 09:59:07 maggiesimpson gnome-keyring-daemon[2488]: couldn't find secret store module: (unknown)
Nov  8 09:59:07 maggiesimpson gnome-keyring-daemon[2488]: lookup_login_keyring: assertion `GCK_IS_SESSION (session)' failed
Nov  8 09:59:07 maggiesimpson gnome-keyring-daemon[2488]: create_credential: assertion `GCK_IS_SESSION (session)' failed
Nov  8 09:59:07 maggiesimpson gnome-keyring-daemon[2488]: egg_error_message: assertion `error' failed
Nov  8 09:59:07 maggiesimpson gnome-keyring-daemon[2488]: couldn't create new login credential: (unknown)
Nov  8 09:59:07 maggiesimpson passwd[2479]: gkr-pam: couldn't change password for the login keyring: the passwords didn't match.
Nov  8 10:17:01 maggiesimpson CRON[2531]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  8 10:17:01 maggiesimpson CRON[2531]: pam_unix(cron:session): session closed for user root
Nov  8 11:17:01 maggiesimpson CRON[2649]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  8 11:17:01 maggiesimpson CRON[2649]: pam_unix(cron:session): session closed for user root
Nov  8 11:18:32 maggiesimpson pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Nov  8 11:18:32 maggiesimpson pkexec: pam_ck_connector(polkit-1:session): cannot determine display-device
Nov  8 11:18:32 maggiesimpson pkexec[2873]: maggiesimpson: Executing command [USER=root] [TTY=unknown] [CWD=/home/maggiesimpson] [COMMAND=/usr/lib/gnome-settings-daemon/gsd-backlight-helper --set-brightness 3]
Nov  8 11:20:47 maggiesimpson pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Nov  8 11:20:47 maggiesimpson pkexec: pam_ck_connector(polkit-1:session): cannot determine display-device
Nov  8 11:20:47 maggiesimpson pkexec[3087]: maggiesimpson: Executing command [USER=root] [TTY=unknown] [CWD=/home/maggiesimpson] [COMMAND=/usr/lib/gnome-settings-daemon/gsd-backlight-helper --set-brightness 6]
Nov  8 11:20:47 maggiesimpson su[3111]: Successful su for maggiesimpson by root
Nov  8 11:20:47 maggiesimpson su[3111]: + ??? root:maggiesimpson
Nov  8 11:20:47 maggiesimpson su[3111]: pam_unix(su:session): session opened for user maggiesimpson by (uid=0)
Nov  8 11:20:48 maggiesimpson su[3111]: pam_unix(su:session): session closed for user maggiesimpson

---

### Post by dannyboy79 on 2012-11-09
sure, go ahead.

---

### Post by Dural on 2012-11-12
dannyboy79,

I've added my log to my previous post.

---

### Post by dannyboy79 on 2012-11-12
i dont see anything unusual besides this:
Nov 8 09:59:07 maggiesimpson gnome-keyring-daemon[2488]: couldn't create new login credential: (unknown)
Nov 8 09:59:07 maggiesimpson passwd[2479]: gkr-pam: couldn't change password for the login keyring: the passwords didn't match.

were you having trouble changing your password? I don't see any outside attempts thru ssh or other to access your system. Maybe someone else can help?

---

### Post by Dural on 2012-11-13
^ I think that time I was trying to login and I got my password wrong. Wish I could use my fingerprint scanner but I'm not sure if there's drivers for it.

---

### Post by dannyboy79 on 2012-11-13
was this box that popped up in the lower right hand corner? if it was, i was just in another thread where a person said it's normal behavior. I think the thread was titled Ubuntu Desktop Intrusion.

---

### Post by Dural on 2012-11-14
I think this was still on the login screen. There were no unusual dialogs. 

Here's what happened:

My computer locked up except for the mouse cursor

I restarted lightdm using the console (Alt-F2)

I logged back in. Every thing was fine. 

I get up to check something downstairs in my house.

I come back and it's in the console (black screen, white text, DOS-looking place). It's displaying some messages like when you shut down the computer in Linux. The part where it checks to make sure everything is shutting down properly.

Except I did not shut down my computer. My old password was displayed in the middle of the screen.

I tried doing **sudo service lightdm restart** as designated in this answer:
[http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes](http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes)

But nothing happened. So I just powered off my computer and turned it back on. From that point everything worked normally but I am not sure as to why that happened. That was why I changed my password just to be safe.

---

### Post by dannyboy79 on 2012-11-14
ok, well I have no idea what happened to you. SOrry I can't help

---

### Post by Dural on 2012-11-14
It seems it was a bug then. How can I report this so it can be looked at?

---

### Post by dannyboy79 on 2012-11-15
> **Dural said:**
> It seems it was a bug then. How can I report this so it can be looked at?you can try reporting it on launchpad ubuntu bugs (google it) but if its not reproducable easily it'll probably go unfixed and just passed off as a little hiccup.

---

