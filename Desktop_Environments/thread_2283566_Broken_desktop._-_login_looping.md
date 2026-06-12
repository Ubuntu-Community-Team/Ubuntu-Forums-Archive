---
title: "Broken desktop. - login looping"
date: 2015-06-22
forum: Desktop Environments
---

### Post by Raymond_van_Driel on 2015-06-22
Hello, and thanks.

New to Linux (obviously, as I have apparently done something very stupid).

Running in VMware.

Logged in to GUI, started a terminal and typed something like "sudo su" <pass>, and "startx".   OS/VM hung.
Restart.  X starts, but Login with my user cycles back to the login screen (after playing drums sound)
Can run other text terminals etc using same user. (eg, with CTRL ALT F2)
How can I recover my desktop?

Ray.

---

### Post by steeldriver on 2015-06-22
Hello and welcome to the forums

From the CTRL ALT F2 (or other) virtual terminal, check the ownership and permissions of your .Xauthority and .ICEauthority hidden files e.g.

```

ls -l ~/.{ICE,X}authority

```

They need to be owned by and writeable by the account owner else the desktop session can't start

---

### Post by Raymond_van_Driel on 2015-06-22
-rw------- 1 dabade  dabade 9540 /home/dabade/.ICEauthority   - (me)
-rw------- 1 root      root       151 /home/dabade/.Xauthority

So that's correct, right?

Thanks, Ray.

---

### Post by steeldriver on 2015-06-23
No, .Xauthority needs to be owned by you - either delete it (it will be regenerated on next successful X session start) or

```

sudo chown dabade:dabade /home/dabade/.Xauthority

```

---

### Post by Raymond_van_Driel on 2015-06-23
That did it, thanks.

---

