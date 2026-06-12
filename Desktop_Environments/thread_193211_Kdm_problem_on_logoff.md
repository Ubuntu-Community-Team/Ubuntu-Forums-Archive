---
title: "Kdm problem on logoff"
date: 2006-06-09
forum: Desktop Environments
---

### Post by meimato on 2006-06-09
I have problems with shutdown/reboot/logoff.
I've got and ATI card, and I used the fglrx drivers; every time I closed the session the screen became black, and system stopped respondig. I found it to be a video driver related issue, and then I replaced the fglrx with ordinary ati driver.
Now I can safely shotdown and reboot, but if I logoff I see two blanking pixels on the kdm screen, and the keyboard doesn't respond: if I try to write my password to logon again nothing happens. The only thing I can do is to switch to console, to reboot the system.

---

### Post by RavenOfOdin on 2006-06-09
I'm having that problem too, but I don't want to switch to ATI drivers 'cause I need OpenGL enabled.

---

### Post by indeed on 2008-04-03
I've had this problem since upgrading to Hardy x64.

This worked for me ...

```
sudo invoke-rc.d atieventsd stop
sudo update-rc.d -f atieventsd remove
```

I'd also blacklisted intel_agp (I have no agp slot) but I'm not sure if that's relevant.

---

