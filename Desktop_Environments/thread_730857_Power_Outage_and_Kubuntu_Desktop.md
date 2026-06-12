---
title: "Power Outage and Kubuntu Desktop"
date: 2008-03-21
forum: Desktop Environments
---

### Post by FofBorg on 2008-03-21
I got a power outage here that created a very weird effect...

When I get my login screen, the system authenticate my users correctly but closes the session witout error right away...

I tested putting bad password and the system gives me a failed login, so I know it successfully loged the user, but if I type a good username / password combination, the screen goes black for some time (about 4 seconds) and go back to the login screen...

If I look at the /var/log/auth.log file, here is what I see..

Mar 21 10:43:16 subversion kdm: :0[6184]: pam_unix(kdm:session): session opened for user sysadmin by (uid=0)
Mar 21 10:43:17 subversion kdm: :0[6184]: pam_unix(kdm:session): session closed for user sysadmin

There is no other errors, nothing...  It looks like a corrupted cash of some type, but I'm not sure where KDE is storing it's things...

I flushed the /tmp directory completly from an openSSH session, did a reboot, to no avail...

Is there any other place or any other logs that could give me some clues as to what is going on ??? 

 HELP...

---

### Post by FofBorg on 2008-03-21
Captain's log, suplemental...

After checking more logs, here is what I found...

sysadmin@subversion:/var/log$ cat kdm.log
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(WW) intel(0): Failed to set up write-combining range (0xe0000000,0x10000000)
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux subversion.fbli.com 2.6.22-14-server #1 SMP Tue Feb 12 08:27:05 UTC 2008 i686
Build Date: 18 January 2008
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 21 11:31:09 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
(II) Module already built-in
(II) Module already built-in
(WW) intel(0): Failed to set up write-combining range (0xe0000000,0x10000000)
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(WW) intel(0): Failed to set up write-combining range (0xe0000000,0x10000000)
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(WW) intel(0): Failed to set up write-combining range (0xe0000000,0x10000000)
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
sysadmin@subversion:/var/log$


Anyone seen this and know what it means ???

---

