---
title: "100% cpu usage none programs open, here big mistery"
date: 2009-06-13
forum: General Help
---

### Post by gabak on 2009-06-13
ubuntu 9.04 with all upgrades downloaded already.!!
SYSTEM MONITOR  say i m using 100% as picture shows but TOP say the oppsite.
and i have CPU FRECUENCY SCALING MONITOR that tells me i m 100% too.
i got a dell laptop so i have it set on demand and it is on 1,87ghz all the time.
few days ago everything was fine and today suddenly that happen.
other thing i see is the cpu fan is on all the time cuz of this.
here it the screen shot i hope somebody can resolve this mistery.

ps: i know how to stop a process with kill or top option K , but how can i kill a process that i cant see?

---

### Post by lovinglinux on 2009-06-13
Go to "System >> Preferences >> Startup Applications", disable "Remote Desktop" and reboot.

BTW, the System Monitor says you are using 100% CPU but TOP says the opposite, because the System Monitor itself is a huge CPU eater.

---

### Post by gabak on 2009-06-15
it worked , thank you so much , now the there is o ther question why that happend? that means i cant use remote desktop? why it is comsuming that much cpu ? and why top did nt show it up on screen?

> **lovinglinux said:**
> Go to "System >> Preferences >> Startup Applications", disable "Remote Desktop" and reboot.

BTW, the System Monitor says you are using 100% CPU but TOP says the opposite, because the System Monitor itself is a huge CPU eater.

---

### Post by QIII on 2009-06-15
There seems to be a bug in vino in Jaunty.

The work around I have seen is to use x11vnc instead.

---

### Post by lovinglinux on 2009-06-15
> **QIII said:**
> There seems to be a bug in vino in Jaunty.

The work around I have seen is to use x11vnc instead.

Better than that would be to use ssh instead, which is much more secure. Remote Desktop is not secure.

---

