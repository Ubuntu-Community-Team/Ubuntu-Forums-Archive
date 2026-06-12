---
title: "Finetuning FreeNX / NXServer"
date: 2008-10-29
forum: Desktop Environments
---

### Post by majkball on 2008-10-29
Hi,

I have followed the suggestions in this thread:
[http://ubuntuforums.org/showthread.php?t=467219](http://ubuntuforums.org/showthread.php?t=467219)
And go FreeNX up and running. However there is a small issue, I get authenticated when I login but no display I showed. I guess this is related to me not having setup what displays to forward with FreeNX. Any suggestions.

This is printout from "sudo nxsetup --test"
```
----> Testing your nxserver configuration ...
Warning: Could not find nxdesktop in /usr/lib/nx. RDP sessions won't work.
Warning: Could not find nxviewer in /usr/lib/nx. VNC sessions won't work.
Warning: Invalid value "APPLICATION_LIBRARY_PRELOAD=/usr/lib/libX11-nx.so.6.2:/u                                                sr/lib/libXext-nx.so.6.4:/usr/lib/libXcomp.so:/usr/lib/libXcompext.so:/usr/lib/l                                                ibXcompshad.so:/usr/lib/libXrender-nx.so.1". /usr/lib/libXcomp.so could not be f                                                ound. Users will not be able to run a single application in non-rootless mode.
Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
         Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
         Users will not be able to request a CDE session.
Warning: Invalid value "COMMAND_SMBMOUNT=smbmount". You'll not be able to use SA                                                MBA.
Warning: Invalid value "COMMAND_SMBUMOUNT=smbumount". You'll not be able to use                                                 SAMBA.
Error: Could not find 1.5.0 or 2.[01].0 or 3.[01].0 version string in nxagent. N                                                X 1.5.0 or 2.[01].0 or 3.[01].0 backend is needed for this version of FreeNX.

  Errors occured during config check.
  Please correct the configuration file.

```

This is how the details look from my client log:
```
Info: Proxy running in client mode with pid '472'.
Session: Starting session at 'Wed Oct 29 17:56:41 2008'.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-kde'. Assuming agent session.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Info: Using pack method 'adaptive-7' with session 'unix-kde'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '11001'.
Session: Session started at 'Wed Oct 29 17:56:43 2008'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Wed Oct 29 17:56:44 2008'.
Session: Session terminated at 'Wed Oct 29 17:56:44 2008'.
```

I am running everything on a fresh out of the box installation of Ubuntu Hardy Heron 8.04

// Mike

---

### Post by majkball on 2008-10-29
Hi,

I knew it was something obvious.

I assumed my Ubuntu server was using KDE but it was Gnome, adjusted the settings in my client software and now everything works flawlessy.

// Mike

---

