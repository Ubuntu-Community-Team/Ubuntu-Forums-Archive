---
title: "Beryl Borders Flicker"
date: 2006-10-31
forum: Desktop Environments
---

### Post by igknighted on 2006-10-31
I just installed Beryl on a fresh install of Kubuntu Dapper, and now all of the borders of my windows flicker.  Everything seems to work OK otherwise, but it is really annoying and hard to work with it.  Any idea how to fix this?

EDIT: I have an x800GTO w/ the fglrx drivers (using xgl, not aiglx obviously)

---

### Post by tribaal on 2006-10-31
The problem is due to the fact that somehow Emerald themer gets started twice. It should hopefully be fixed in the next update.

A quick workaround (that worked for me) is to add "emerald" to your session startup script:

System > Preferences > Sessions > Startup programs
And add "emerald" (without quotes).

Please let me know if this helped...

- trib'

---

### Post by igknighted on 2006-10-31
> **tribaal said:**
> The problem is due to the fact that somehow Emerald themer gets started twice. It should hopefully be fixed in the next update.

A quick workaround (that worked for me) is to add "emerald" to your session startup script:

System > Preferences > Sessions > Startup programs
And add "emerald" (without quotes).

Please let me know if this helped...

- trib'

I am in KDE, where do I find this?

---

### Post by tribaal on 2006-10-31
Excellent question. Unfortunately I'm a hardcore GNOME user, so I have no idea :(

Hope somebody else will be able to answer :(

- trib'

---

### Post by igknighted on 2006-10-31
In the mean time I have disabled blur effects, which has helped a little (doesn't flicker, but I have no window borders), but won't work permanently.

---

### Post by igknighted on 2006-11-01
Sorry to double post, but having rebooted about 5 times (but changed nothing except the menu.lst section dealing with my gentoo disk) the problem has mysteriously gone away... go figure.

---

### Post by iserlohn on 2006-11-01
You might want to check your sessions and make sure that the only beryl/emerald commands in the list are -

beryl-xgl
beryl-manager

I've done several installations and this fixes it.

---

### Post by zgornel on 2006-11-01
> **tribaal said:**
> The problem is due to the fact that somehow Emerald themer gets started twice. It should hopefully be fixed in the next update.

A quick workaround (that worked for me) is to add "emerald" to your session startup script:

System > Preferences > Sessions > Startup programs
And add "emerald" (without quotes).

Please let me know if this helped...

- trib'
Yep, that's exactely what I did. Strange how people find the same solutions. :D

---

### Post by Noxion on 2006-11-13
> **igknighted said:**
> I am in KDE, where do I find this?

Im in the same positionw ith the same problem, anyone care to help?

---

