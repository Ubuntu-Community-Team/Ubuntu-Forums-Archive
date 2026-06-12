---
title: "gdm is only half alive"
date: 2009-03-27
forum: General Help
---

### Post by D-Dan on 2009-03-27
Hi guys

As much as I'm hoping Ubuntu will eventually replace win - the very fact that it is so configurable is still killing me.

I was quite happy with a gnome desktop and gdm, but I had to install kde just to see.

Now, kde is very nice, but suffers some problems that I can't fix and so I'm happy to go back to Gnome/gdm. the problem is, whilst before the kde experiment, gnome would quite happily start with auto login, the only way I can start it with gdm is getting tiresome.

I want gdm back on auto login. My problem is that now I get left at a terminal window, where I have to login, then start x with sudo gdm before I get my desktop back.

After that it's happy, but how do I get back to how it was before the kde experiment?

I've tried some more obvious solutions found on the web (edited /etcX11/default-display-manager to use gdm - didn't work), dpkg -reconfigure etc, but no joy.

Any help?

TIA:confused:

---

### Post by Dr Small on 2009-03-27
Did you try this?
```
sudo dpkg-reconfigure gdm
```

---

### Post by D-Dan on 2009-03-28
Yep. Didn't work :(

---

### Post by DeMus on 2009-03-28
> **D-Dan said:**
> Hi guys

As much as I'm hoping Ubuntu will eventually replace win - the very fact that it is so configurable is still killing me.

I was quite happy with a gnome desktop and gdm, but I had to install kde just to see.

Now, kde is very nice, but suffers some problems that I can't fix and so I'm happy to go back to Gnome/gdm. the problem is, whilst before the kde experiment, gnome would quite happily start with auto login, the only way I can start it with gdm is getting tiresome.

I want gdm back on auto login. My problem is that now I get left at a terminal window, where I have to login, then start x with sudo gdm before I get my desktop back.

After that it's happy, but how do I get back to how it was before the kde experiment?

I've tried some more obvious solutions found on the web (edited /etcX11/default-display-manager to use gdm - didn't work), dpkg -reconfigure etc, but no joy.

Any help?

TIA:confused:

Log out.
At the Welcome screen click on Options and choose Gnome. Also click-on the line that asks if you always want to use Gnome.
Then log in with name and password.
If autologin is set then the next time you will be able to log-in automatically.
Now uninstall KDE in Synaptic and you are done.

---

