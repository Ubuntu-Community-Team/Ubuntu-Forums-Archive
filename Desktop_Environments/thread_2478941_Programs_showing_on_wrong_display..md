---
title: "Programs showing on wrong display."
date: 2022-09-09
forum: Desktop Environments
---

### Post by Phill_Harvey-Smith on 2022-09-09
Hi all,

I have an intel NUC that is running Ubuntu 22.04.1 LTS. If I login to the desktop on the machine as user phill, but also ssh in as the same user from another machine (windows running Cygwin-X), some X programs will send their display to the wrong screen.

e.g. pluma or geany launched from the ssh session opens the window on the console seesion, not on the windows session. However xclock works fine, I get the clock on the windows X session.

(From Cygwin X shell)

ssh phill@nuc -Y
--enter password--
pluma  (output fires up on console window, not cygwin, ctrl-c to close)
xclock (output fires up on cygwin-x as required).

If I logout from my session on the console then pluma & geany work as expected.

Is there any way to fix this?

Cheers.

Phill.

---

### Post by TheFu on 2022-09-09
Use:
```
$ ssh -X user@server command
```

This will enable X11 forwarding and set the DISPLAY correctly.
You might see 
```
$ ssh -Y user@server command
```
too. I always have to check the manpage for the subtle differences.

I have to admit, I haven't used cygwin since the 1990s.  I found a light Linux with X/Windows to be a much better X/Server than any of the hacks running X on MS-Windows.  That includes expensive, corporate, X/Windows application suites.

---

### Post by Phill_Harvey-Smith on 2022-09-09
I have tried -X and -Y and get the same reults, window opens on wrong display.

If I echo $DISPLAY from the ssh session I get localhost:11.0 which seems reasonable.

The odd thing is that the forwarding works fine for things like xclock, xman etc, but not for pluma, geany.

I have just also tried connecting via ssh from an OpenSuSE box (to try and illiminate cygwin-x as the cause) , 
which also results in the window opening on the wrong display.

Doing the same TO the suse box, and everything opens correctly.

Cheers.

Phill.

---

### Post by TheFu on 2022-09-09
Wayland or Xorg?

Xorg will fully honor the DISPLAY, but I don't know what Wayland uses or even if it supports remote stuff.

---

### Post by Phill_Harvey-Smith on 2022-09-09
Ahaaa!

Seems I was running wayland, switching it to xorg has enabled it to work as expected.

Cheers.

Phill.

---

### Post by TheFu on 2022-09-09
> **Phill_Harvey-Smith said:**
> Ahaaa!

Seems I was running wayland, switching it to xorg has enabled it to work as expected.

Cheers.

Phill.

Great.  Please help the community out by marking this thread as SOLVED - "Thread Tools" button/link near the top of the screen. It will keep people from wasting time.

---

### Post by Phill_Harvey-Smith on 2022-09-10
> **TheFu said:**
> Great.  Please help the community out by marking this thread as SOLVED - "Thread Tools" button/link near the top of the screen. It will keep people from wasting time.

Done!

Cheers.

Phill.

---

