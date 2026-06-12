---
title: "KDM will not spawn a new login window upon logout"
date: 2009-07-06
forum: Desktop Environments
---

### Post by spencer3096 on 2009-07-06
Hello.

I am using a default install of Kubuntu 9.04 on a Dell Optiplex GX-240, and whenever any user on the system logs out, the system neither spawns a new login window nor goes to a textual login screen.  The only thing displayed is the startup messages that are shown right before the KDM login screen is brought up, and the X server is shut down completely.  I am able to switch users, but if everyone has logged out, the only solution that I have found is to switch to another tty, login, and start X manually.

I have attached my kdmrc, backgroundrc, and xorg.conf files in case the problem lies there.

Thank you for any help that you can provide.

---

### Post by linuxgirlie on 2010-01-28
Oops sorry I am not getting the same problem.

---

### Post by Zorael on 2010-01-28
Intel graphics?

The intel driver in 9.04 has a bug that makes X segfault when trying to regenerate its session. Basically, when logging out it tries to unload everything and go back to the login screen, to reuse the loaded modules, drivers, etc. A workaround is to tell it to end the X process and start a completely new one.

Add the following line (in bold) under the **[X-:*-Core]** header in your kdmrc.
```
# Restart instead of resetting the local X-server after session exit.
# Use it if the server leaks memory etc.
# Default is false
**TerminateServer=true**
```

---

### Post by Capoeira on 2010-03-05
> **Zorael said:**
> Intel graphics?

The intel driver in 9.04 has a bug that makes X segfault when trying to regenerate its session. Basically, when logging out it tries to unload everything and go back to the login screen, to reuse the loaded modules, drivers, etc. A workaround is to tell it to end the X process and start a completely new one.

Add the following line (in bold) under the **[X-:*-Core]** header in your kdmrc.
```
# Restart instead of resetting the local X-server after session exit.
# Use it if the server leaks memory etc.
# Default is false
**TerminateServer=true**
```

I have the same problem.....this doesn't fix

i have no intel-grafics

after logout i get a text-login BUT i can't even login....it alqays says wrong user or password....

only Ctrl+Alt+Delete resolves (reboot)

---

### Post by Capoeira on 2010-03-05
after seeing the kdmrc the idea came to me: automatic login was disabled BUT my user needs to type no password....could it be the problem?

yes, it was the problem...disabled the my user dont no password and kdm restarts normaly

---

### Post by Capoeira on 2010-03-06
I swear it worked but now it doesn't anymore

---

### Post by bunnyhugh on 2010-03-11
> **Capoeira said:**
> I swear it worked but now it doesn't anymore

Don't know if you are still are having a problem. But if your are try changing the kdm theme with the login manager from system settings, I had the same problem, and it was because some how the theme had got deleted, so when I logged out the system just hung trying to load a non-existent login theme. I didn't notice it on boot because my system is set to auto login.

---

### Post by Capoeira on 2010-03-11
> **bunnyhugh said:**
> Don't know if you are still are having a problem. But if your are try changing the kdm theme with the login manager from system settings, I had the same problem, and it was because some how the theme had got deleted, so when I logged out the system just hung trying to load a non-existent login theme. I didn't notice it on boot because my system is set to auto login.

No, that's not the problem here. I don't have the auto-login anymore.

It's not that kind of big problem though as i am the only user, only need it (logging out) from time to time for changing to fluxbox when i do audio-work

---

### Post by OldGaf on 2011-03-22
> **Zorael said:**
> Intel graphics?

The intel driver in 9.04 has a bug that makes X segfault when trying to regenerate its session. Basically, when logging out it tries to unload everything and go back to the login screen, to reuse the loaded modules, drivers, etc. A workaround is to tell it to end the X process and start a completely new one.

Add the following line (in bold) under the **[X-:*-Core]** header in your kdmrc.
```
# Restart instead of resetting the local X-server after session exit.
# Use it if the server leaks memory etc.
# Default is false
**TerminateServer=true**
```

Excellent!
This was an issue for me with Kubuntu 10.10 as well.... this fixed it for me. \\:D/

---

