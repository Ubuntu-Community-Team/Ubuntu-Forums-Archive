---
title: "Waiting for gdm"
date: 2008-08-24
forum: Desktop Environments
---

### Post by HamRadio64 on 2008-08-24
Hi,

I have a problem with gdm on my wife's Asus eeePC 701 running Ubuntu Hardy with a custom 2.6.26.2 vanilla kernel, XFCE-4.4.2 and gdm 2.20.7-0ubuntu1.1.

Gdm works fine until the login request, then I pick the user from the list and I type the password. At this point it freezes for about 30 seconds before starting the desktop manager (XFCE).

I have this delay only if the configured "default gateway" is not reachable, which can be because the ethernet cable is unplugged, because there is no wireless connection, or because network parameters have been set for the work office (where there is a dhcp server) while being at home (where I have a static ip configuration), and so on...

There is no delay if the "default gateway" is reachable.

I've enabled "debug" in gdmsetup so I get the following messages in /var/log/syslog when the delay occurs:

Aug 23 10:41:14 eee gdm[3884]: DEBUG: Sending GREETPID == 0 for slave 3884 
Aug 23 10:41:14 eee gdm[3883]: DEBUG: Attempting to parse key string: debug/Enable=false 
Aug 23 10:41:14 eee gdm[3883]: DEBUG: Handling message: GREETPID 3884 0' 
Aug 23 10:41:14 eee gdm[3883]: DEBUG: Got GREETPID == 0 
Aug 23 10:41:14 eee gdm[3884]: DEBUG: Attempting to parse key string: daemon/KillInitClients=true 
Aug 23 10:41:14 eee gdm[3884]: DEBUG: Attempting to parse key string: daemon/SessionDesktopDir=/etc/X11/sessions/:/etc/dm/Sessions/:/usr/share/gdm/BuiltInSessions/:/usr/share/xsessions/ 
Aug 23 10:41:14 eee gdm[3884]: DEBUG: Attempting to parse key string: Desktop Entry/X-Gdm-XserverArgs 

[here is the delay]

Aug 23 10:41:42 eee gdm[3884]: DEBUG: get_local_auths: Setting up socket access 
Aug 23 10:41:42 eee gdm[3884]: DEBUG: get_local_auths: Setting up network access 
Aug 23 10:41:42 eee gdm[3884]: DEBUG: Attempting to parse key string: debug/Enable=false 
Aug 23 10:41:42 eee gdm[3884]: DEBUG: get_local_auths: Setting up access for :0 - 6 entries 
Aug 23 10:41:42 eee gdm[3884]: DEBUG: gdm_auth_user_add: Adding cookie for 501 
Aug 23 10:41:42 eee gdm[3884]: DEBUG: Attempting to parse key string: daemon/UserAuthDir= 
Aug 23 10:41:42 eee gdm[3884]: DEBUG: Attempting to parse key string: daemon/UserAuthFile=.Xauthority 
Aug 23 10:41:42 eee gdm[3884]: DEBUG: Attempting to parse key string: security/RelaxPermissions=0 
Aug 23 10:41:42 eee gdm[3884]: DEBUG: Attempting to parse key string: security/UserMaxFile=65536 
Aug 23 10:41:42 eee gdm[3884]: DEBUG: Attempting to parse key string: security/SupportAutomount=false 
Aug 23 10:41:42 eee gdm[3884]: DEBUG: Attempting to parse key string: security/CheckDirOwner=true 
Aug 23 10:41:42 eee gdm[3884]: DEBUG: Attempting to parse key string: security/NeverPlaceCookiesOnNFS=true 
Aug 23 10:41:42 eee gdm[3884]: DEBUG: gdm_auth_user_add: Using /home/ric/.Xauthority for cookies 

If I disable gdm and I login in the console, then I run "startx" there is no delay.

I've tried changing some preferences in gdmsetup, like changing the default session from running XFCE directly and/or running my .xsession script (which is a link to .xinitrc so that I have the same programs started by "startx").

The problem is always there even when booting with the stock "generic" ubuntu kernel.

I can figure out it should be something related to some kind of 
authorizations that gdm perhaps could ask to a non-existent server and then awaits the time out, or something related to pam and the files /etc/pam.d/gdm*...

I've no clue about how to solve the problem, so I'm postig here hoping someone could perhaps help me.

Many thanks in advance.

---

