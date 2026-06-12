---
title: "gdm power button and the 60 seconds to shutdown"
date: 2010-02-24
forum: Desktop Environments
---

### Post by zyphos on 2010-02-24
Hi,
my problem is not the one with the menu->shutdown.

I am using Ubuntu Karmic 9.10, when you are at login screen (GDM), and press you computer power button, a dialog shows up with 60 seconds to shutdown.

How can I disable this dialog and shutdown immediately like before Ubuntu 9.10 ?

Thank you for any anwser or suggestion.

---

### Post by donverse on 2010-02-24
It's somewhere in the system preferences, I'm not 100% sure where, but I know that I found it ;)

Just take a look at it, I'm sure you'll find it..

---

### Post by hariks0 on 2010-02-24
Applications > System tools > GConfig editor > /apps/indicator-session/suppress_logout_restart_shutdown = Enable.

---

### Post by zyphos on 2010-03-08
> **hariks0 said:**
> Applications > System tools > GConfig editor > /apps/indicator-session/suppress_logout_restart_shutdown = Enable.

That was already done. Thank you anyway for anwser but like I wrote in my first post, I am NOT talking about the 60 seconds when you are logged in (your solution is for that one), but 60 seconds at the Login Screen. (when you need to choose your username)

---

### Post by rioch on 2010-03-12
Did you find a solution to this problem?

---

### Post by zyphos on 2010-03-12
No I am still looking for. For now I have to wait 60 secs (for virtual machine shutdown) every time I shutdown my computer.

---

