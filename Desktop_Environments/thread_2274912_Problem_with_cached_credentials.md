---
title: "Problem with cached credentials"
date: 2015-04-23
forum: Desktop Environments
---

### Post by capman on 2015-04-23
Ive been trying to set up a desktop enviroment of ubuntu with, userinformation from kerberos (krb5), ldap and cached credentials. It works fine while connected through ethernet or wireless.
But when im offline I get some strange errors.

While offline, when trying to log in, it seems to be okay but then it loop's me back to loginscreen, and there's a notice that says "you have been logged in with cached credentials" from where you have to press enter again to get pass it. Its only after 2nd or 3rd try that the login succeds. And i cant make heads or tails from it.

The packages im using are heimdal-clients openafs-krb5 nslcd nss-updatedb libpam-cracklib libpam-ldap libpam-ccreds libnss-ldapd

Here's what the auth log file says:

> Apr 23 10:49:34 A2644 compiz: pam_krb5(unity:auth): authentication failure; logname=capman uid=14813 euid=14813 tty= ruser= rhost=Apr 23 10:49:34 A2644 compiz: pam_unix(unity:auth): authentication failure; logname= uid=14813 euid=14813 tty= ruser= rhost=  user=capman
Apr 23 10:49:34 A2644 compiz: gkr-pam: unlocked login keyring
Apr 23 10:49:37 A2644 polkitd(authority=local): Unregistered Authentication Agent for unix-session:c4 (system bus name :1.85, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)
Apr 23 10:49:48 A2644 sshd[829]: Server listening on 0.0.0.0 port 22.
Apr 23 10:49:48 A2644 sshd[829]: Server listening on :: port 22.
Apr 23 10:50:04 A2644 lightdm: pam_kwallet(lightdm-greeter:setcred): pam_sm_setsecred
Apr 23 10:50:04 A2644 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Apr 23 10:50:04 A2644 lightdm: pam_kwallet(lightdm-greeter:session): pam_sm_open_session
Apr 23 10:50:04 A2644 lightdm: pam_kwallet(lightdm-greeter:session): pam_kwallet: open_session called without kwallet_key
Apr 23 10:50:07 A2644 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "capman"
Apr 23 10:50:09 A2644 lightdm: pam_krb5(lightdm:auth): authentication failure; logname=capman uid=0 euid=0 tty=:0 ruser= rhost=
Apr 23 10:50:09 A2644 lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=capman
Apr 23 10:50:09 A2644 lightdm: pam_kwallet(lightdm:auth): pam_sm_authenticate
Apr 23 10:50:10 A2644 lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Apr 23 10:50:10 A2644 lightdm: pam_kwallet(lightdm-greeter:session): pam_sm_close_session
Apr 23 10:50:10 A2644 lightdm: pam_kwallet(lightdm-greeter:setcred): pam_sm_setsecred
Apr 23 10:50:10 A2644 lightdm: pam_kwallet(lightdm:setcred): pam_sm_setsecred
Apr 23 10:50:10 A2644 lightdm: pam_unix(lightdm:session): session opened for user capman by (uid=0)
Apr 23 10:50:10 A2644 lightdm: pam_kwallet(lightdm:session): pam_sm_open_session
Apr 23 10:50:10 A2644 lightdm: pam_kwallet(lightdm:session): pam-kwallet: final socket path: /tmp//capman.socket
Apr 23 10:50:10 A2644 gnome-keyring-daemon[1544]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
Apr 23 10:50:13 A2644 lightdm: pam_unix(lightdm:session): session closed for user capman
Apr 23 10:50:13 A2644 lightdm: pam_kwallet(lightdm:session): pam_sm_close_session
Apr 23 10:50:13 A2644 lightdm: pam_kwallet(lightdm:setcred): pam_sm_setsecred
Apr 23 10:50:13 A2644 lightdm: pam_kwallet(lightdm-greeter:setcred): pam_sm_setsecred
Apr 23 10:50:13 A2644 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Apr 23 10:50:13 A2644 lightdm: pam_kwallet(lightdm-greeter:session): pam_sm_open_session
Apr 23 10:50:13 A2644 lightdm: pam_kwallet(lightdm-greeter:session): pam_kwallet: open_session called without kwallet_key
Apr 23 10:50:16 A2644 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "capman"
Apr 23 10:50:17 A2644 lightdm: pam_krb5(lightdm:auth): authentication failure; logname=capman uid=0 euid=0 tty=:0 ruser= rhost=
Apr 23 10:50:17 A2644 lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=capman
Apr 23 10:50:17 A2644 lightdm: pam_kwallet(lightdm:auth): pam_sm_authenticate
Apr 23 10:50:18 A2644 lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Apr 23 10:50:18 A2644 lightdm: pam_kwallet(lightdm-greeter:session): pam_sm_close_session
Apr 23 10:50:18 A2644 lightdm: pam_kwallet(lightdm-greeter:setcred): pam_sm_setsecred
Apr 23 10:50:18 A2644 lightdm: pam_kwallet(lightdm:setcred): pam_sm_setsecred
Apr 23 10:50:18 A2644 lightdm: pam_unix(lightdm:session): session opened for user capman by (uid=0)
Apr 23 10:50:18 A2644 lightdm: pam_kwallet(lightdm:session): pam_sm_open_session
Apr 23 10:50:18 A2644 lightdm: pam_kwallet(lightdm:session): pam-kwallet: final socket path: /tmp//capman.socket
Apr 23 10:50:18 A2644 gnome-keyring-daemon[2274]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
Apr 23 10:50:18 A2644 gnome-keyring-daemon[2274]: message repeated 2 times: [ couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files]
Apr 23 10:50:18 A2644 gnome-keyring-daemon[2274]: The GPG agent was already initialized
Apr 23 10:50:18 A2644 gnome-keyring-daemon[2274]: The SSH agent was already initialized
Apr 23 10:50:18 A2644 gnome-keyring-daemon[2274]: The PKCS#11 component was already initialized
Apr 23 10:50:18 A2644 gnome-keyring-daemon[2274]: The Secret Service was already initialized
Apr 23 10:50:19 A2644 polkitd(authority=local): Registered Authentication Agent for unix-session:c4 (system bus name :1.83 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Apr 23 10:50:23 A2644 sudo: pam_krb5(sudo:auth): authentication failure; logname=capman uid=14813 euid=0 tty=/dev/pts/8 ruser=capman rhost=
Apr 23 10:50:23 A2644 sudo: pam_unix(sudo:auth): authentication failure; logname=capman uid=14813 euid=0 tty=/dev/pts/8 ruser=capman rhost=  user=capman
Apr 23 10:50:23 A2644 sudo:   capman : TTY=pts/8 ; PWD=/lhome/capman ; USER=root ; COMMAND=/usr/local/bin/tcsh
Apr 23 10:50:23 A2644 sudo: pam_unix(sudo:session): session opened for user root by capman(uid=0)




---

### Post by dino99 on 2015-04-23
i'm feeling you need to wait for a kwallet fix
some users are recently complaining about it  [http://ubuntuforums.org/showthread.php?t=2274164](http://ubuntuforums.org/showthread.php?t=2274164)

Looks like that 'offline' issue has not been reported yet, please do  [https://bugs.launchpad.net/bugs/+bugs?field.searchtext=kwallet&search=Search%20Bug%20Reports&field.scope=all&field.scope.target=&orderby=-date_last_updated&start=0](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=kwallet&search=Search%20Bug%20Reports&field.scope=all&field.scope.target=&orderby=-date_last_updated&start=0)

---

### Post by capman on 2015-04-23
It seems more like a problem with either lightdm itself or something with the pam-modules, but i cant figure out what. Ive disabled everything in pam regarding kwallet and the computer behaves exactly the same.

> Apr 23 13:36:01 A2644 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "capman"Apr 23 13:36:03 A2644 lightdm: pam_krb5(lightdm:auth): authentication failure; logname=capman uid=0 euid=0 tty=:0 ruser= rhost=
Apr 23 13:36:03 A2644 lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=capman
Apr 23 13:36:04 A2644 lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Apr 23 13:36:04 A2644 lightdm: pam_unix(lightdm:session): session opened for user capman by (uid=0)
Apr 23 13:36:04 A2644 systemd-logind[475]: New session c2 of user capman.
Apr 23 13:36:04 A2644 systemd-logind[475]: Linked /tmp/.X11-unix/X0 to /run/user/14813/X11-display.
Apr 23 13:36:04 A2644 gnome-keyring-daemon[1510]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
Apr 23 13:36:06 A2644 lightdm: pam_unix(lightdm:session): session closed for user capman
Apr 23 13:36:06 A2644 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Apr 23 13:36:06 A2644 systemd-logind[475]: New session c3 of user lightdm.
Apr 23 13:36:07 A2644 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "capman"
Apr 23 13:36:09 A2644 lightdm: pam_krb5(lightdm:auth): authentication failure; logname=capman uid=0 euid=0 tty=:0 ruser= rhost=
Apr 23 13:36:09 A2644 lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=capman
Apr 23 13:36:09 A2644 lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Apr 23 13:36:09 A2644 lightdm: pam_unix(lightdm:session): session opened for user capman by (uid=0)
Apr 23 13:36:09 A2644 systemd-logind[475]: New session c4 of user capman.
Apr 23 13:36:10 A2644 gnome-keyring-daemon[2153]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
Apr 23 13:36:10 A2644 systemd-logind[475]: Removed session c3.
Apr 23 13:36:10 A2644 gnome-keyring-daemon[2153]: message repeated 2 times: [ couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files]
Apr 23 13:36:10 A2644 gnome-keyring-daemon[2153]: The GPG agent was already initialized
Apr 23 13:36:10 A2644 gnome-keyring-daemon[2153]: The SSH agent was already initialized
Apr 23 13:36:10 A2644 gnome-keyring-daemon[2153]: The PKCS#11 component was already initialized
Apr 23 13:36:10 A2644 gnome-keyring-daemon[2153]: The Secret Service was already initialized
Apr 23 13:36:11 A2644 polkitd(authority=local): Registered Authentication Agent for unix-session:c4 (system bus name :1.82 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)




---

### Post by dino99 on 2015-04-23
pam can be that one to blame as you have also pointed. As there is a doubt, report anyway against either kwallet or an installed libpam-xxxx; devs will change the chosen package if they are thinking about something else

---

