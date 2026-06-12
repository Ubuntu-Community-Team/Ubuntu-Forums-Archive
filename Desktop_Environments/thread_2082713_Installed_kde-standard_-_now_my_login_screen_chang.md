---
title: "Installed kde-standard - now my login screen changed - how do I get the old one?"
date: 2012-11-10
forum: Desktop Environments
---

### Post by orange2k on 2012-11-10
Like the title says, when I installed kde-standard it asked me whether I want gdm or kdm, so I chose kdm and then my login screen changed. How do I get my stock login screen back?

Unfortunately I cannot grab a screenshot of my current login screen, but it looks like some kind of mix between gnome-shell and stock ubuntu look...(yes I've installed gnome-shell, too)

---

### Post by 2F4U on 2012-11-10
KDM is the login screen for KDE and you said you wanted it. What is/was your "stock login screen"? The default for Ubuntu would be LightDM, but you don't seem to have a default installation.

---

### Post by orange2k on 2012-11-10
[IMG]http://1.bp.blogspot.com/-WE3KdvhtQCY/T5ZmI4TyDpI/AAAAAAAAIqc/BuD1Ehsk9XE/s320/ubuntu12.04-login-screen.png[/IMG]

this was my "stock" login screen, but I can't find a way to get it to be like that...

---

### Post by PaulW2U on 2012-11-10
In a terminal:

```
sudo dpkg-reconfigure lightdm
```

then tab to lightdm and press enter.

---

### Post by orange2k on 2012-11-10
> **PaulW2U said:**
> In a terminal:

```
sudo dpkg-reconfigure lightdm
```

then tab to lightdm and press enter.

I did that, but I'm still getting something like this:

[IMG]http://i.stack.imgur.com/dHV2J.jpg[/IMG]

There was a solution for this problem in Oneiric - there was the Simple LightDM Manager available, but not so in Precise...

I'm not sure what I did wrong - whatever choice I make in following the step you advised I get the same login screen - I know its not a major issue, but I really like the default login screen...

---

### Post by PaulW2U on 2012-11-10
> **orange2k said:**
> I'm not sure what I did wrong - whatever choice I make in following the step you advised I get the same login screen - I know its not a major issue, but I really like the default login screen...

Did you reboot or just log-out?

If you rebooted then I don't know what the problem is. If you just logged out then while logged out, switch to a tty and enter:

```
sudo stop gdm
sudo start lightdm
```

---

### Post by deadflowr on 2012-11-10
Have you uninstalled anything?
Chances are you'll have to reinstall lightdm, then follow the reconfigure option again.
Look in your package manager and see if lightdm is installed or not.

---

### Post by orange2k on 2012-11-10
Now I'm getting the KDE login screen...

Anyways I'm giving up on this, and besides the KDE login screen is nice, too, so I'm sticking with it...

I'll mark this as solved...

---

