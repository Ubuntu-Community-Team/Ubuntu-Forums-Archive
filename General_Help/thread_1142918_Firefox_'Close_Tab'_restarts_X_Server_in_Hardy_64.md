---
title: "Firefox 'Close Tab' restarts X Server in Hardy 64"
date: 2009-04-29
forum: General Help
---

### Post by bostonaholic on 2009-04-29
This has been happening for the past several weeks, maybe even 2 months.  I'll have several tabs open in FF and I'll click the 'x' to close a tab.  As soon as I do that, it takes me to the login screen as if I did the Ctrl-Alt-BackSpace.

Anyone else have this problem?  I'm running 8.04 64-bit with the most recent FF and all updates.  Is there a log somewhere I could check?

Thanks.

---

### Post by Kareeser on 2009-04-29
Yikes!

Give the syslog a look:
```
cat /var/log/syslog | less
```

---

### Post by bostonaholic on 2009-04-29
> **Kareeser said:**
> Yikes!

Give the syslog a look:
```
cat /var/log/syslog | less
```

Thanks, I'll try that next time it happens.  It doesn't provide any useful information now.

---

### Post by bostonaholic on 2009-05-02
It just happened again.  Here is the output.

```
matthew@gemini ~ > cat /var/log/syslog | less

May  2 18:19:46 gemini kernel: [257186.010327] compiz.real[6236] trap stack segment rip:40fee0 rsp:7fffc2ad1ec0 error:0
May  2 18:19:46 gemini gdm[5776]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
May  2 18:19:49 gemini kernel: [257189.886746] [drm] Setting GART location based on new memory map
May  2 18:19:49 gemini kernel: [257189.887232] [drm] Loading R300 Microcode
May  2 18:19:49 gemini kernel: [257189.887273] [drm] writeback test succeeded in 1 usecs
May  2 18:20:06 gemini pulseaudio[1652]: pid.c: Stale PID file, overwriting.
May  2 18:20:13 gemini NetworkManager: <info>  Updating allowed wireless network lists. 
May  2 18:20:13 gemini NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..
```

---

### Post by spadron on 2009-06-16
I just want to add that I'm having the same problem.

I thought it was when I was loading new pages, but you've just made me realise it's when I'm closing the old tabs :)

---

### Post by bostonaholic on 2009-06-16
> **spadron said:**
> I just want to add that I'm having the same problem.

I thought it was when I was loading new pages, but you've just made me realise it's when I'm closing the old tabs :)

Yay, I'm glad someone else is having the same issue.  What versions of these are you running?

**Ubuntu:** 8.04.2
**Arch:** x86_64
**Gnome:** 2.22.3
**Kernel:** Linux 2.6.24-24-generic
**Fire Fox:** 3.0.11

---

