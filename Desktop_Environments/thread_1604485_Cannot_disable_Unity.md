---
title: "Cannot disable Unity"
date: 2010-10-24
forum: Desktop Environments
---

### Post by thef0rce on 2010-10-24
Hi,

I upgraded to Maverick recently on my netbook. I was using the old netbook remix with the launcher. Unity is too slow and buggy for day to day use. I selected Ubuntu desktop edition in the menu at the login screen and logged in, but Unity started up anyway. Does anyone have any ideas on how to make Unity go away?

Thanks

---

### Post by sanderd17 on 2010-10-24
You clould remove unity, I've done it.

Go in the terminal and execute
```

sudo aptitude search unity

```
and 
```

sudo aptitude search netbook

```

And for every package on which you see an 'i' left to the package name: execute
```

sudo aptitude remove [PACKAGE]

```
with [PACKAGE] the packagename.

Finally, be sure the desktop edition is installed:

```

sudo aptitude install ubuntu-desktop

```

---

### Post by thef0rce on 2010-10-24
I tried just uninstalling it once and had no GUI after login. I think the links on the login screen have been altered. If anyone knows what files actually control the configuration of the login screen, it would be helpful

---

### Post by sanderd17 on 2010-10-24
can you login via the CLI and then execute

```

startx

```

---

### Post by thef0rce on 2010-10-24
how do I login via the CLI in ubuntu? It isn't the recovery console. That has a display manager

---

### Post by sanderd17 on 2010-10-24
sorry, didn't read that good, so you can login via GUI but after your login, you only get a CLI?

well, then execute the startx command.

If you can't login, press CTRL+ALT+F1 and you'll get a way of logging in via the CLI.

---

### Post by thef0rce on 2010-10-24
No. The problem is even if I choose to start up ubuntu desktop and not the netbook version, I get the netbook interface. I don't like Unity, it crashes all the time. I just want to go back to using gnome. I must have messed up the desktop edition link, maybe linked it to something else, but I can't figure out what I did to get to this point.

I've uninstalled unity once and it didn't go well so I reinstalled it and now I'm back to my original problem. So I think there must be a way to solve this without nuking Unity from my system

---

### Post by thef0rce on 2010-10-24
Ha I solved my own problem. At some point I seem to have symlinked the default configuration for gnome to the default configuration for the netbook remix.

For others who may have this problem, the default configuration files are in 
```

/usr/share/gconf/defaults 

```

for the desktop edition. Any symlinks referring to une should be deleted. 

Then do

```

sudo update-gconf-defaults

```

and logout and log back in to the desktop edition and Unity will be gone :)

---

### Post by sanderd17 on 2010-10-24
congrats,

I wouldn't have found this.

---

### Post by mdmcginn on 2011-04-30
The method described only works if your login screen gives you options to log in with a different mode, which mine doesn't. But you can change back to Ubuntu Classic using the Ubuntu System Settings (you can always change it back to Unity later). 

1) Click on the power button in the upper right corner (mine looks like a light switch) and choose the last option, System Settings.
2) Search for Login Screen
3) Double-click to display
4) Choose Unlock and enter your password
5) Select Ubuntu Classic as default session.

---

### Post by 11.04eli on 2011-05-15
You are all wrong. To disable Ubuntu Unity, turn off your computer and turn it back on again (restart) and then select 'Ubuntu Classic Edition' at the bottom. To turn back on, simply change back to 'Ubuntu Desktop Edition' when you log in. :guitar:

---

### Post by llanitedave on 2011-05-15
Thanks for this.  I gave Unity what I consider a fair try, but I couldn't make myself like it.  It's simply too disorganized by default, and too convoluted for me to organize easily.  It's got a bit of growing up to do.

---

### Post by war59312 on 2011-05-15
Agree. It should have asked during the upgrade/install if you wish to use Unity or not.

I hate it! Thanks for the helpful tips. Looking good.

> **11.04eli said:**
> You are all wrong. To disable Ubuntu Unity,  turn off your computer and turn it back on again (restart) and then  select 'Ubuntu Classic Edition' at the bottom. To turn back on, simply  change back to 'Ubuntu Desktop Edition' when you log in. :guitar:Really should watch your language.

That IS wrong too if you want to be like that.

I don't even get that choice, since auto login is enabled.

So the point: Stop assuming everyone else is wrong and only you are right.

---

### Post by pepa007 on 2011-06-21
> **mdmcginn said:**
> The method described only works if your login screen gives you options to log in with a different mode, which mine doesn't. But you can change back to Ubuntu Classic using the Ubuntu System Settings (you can always change it back to Unity later). 

1) Click on the power button in the upper right corner (mine looks like a light switch) and choose the last option, System Settings.
2) Search for Login Screen
3) Double-click to display
4) Choose Unlock and enter your password
5) Select Ubuntu Classic as default session.

this works fine. thanks.

---

### Post by DavidBiesack on 2012-01-04
> **mdmcginn said:**
> 
1) Click on the power button in the upper right corner (mine looks like a light switch) and choose the last option, System Settings.
2) Search for Login Screen
...

I guess I'm hosed because my search for "Login Screen" or "Login" does not match anything. I can see Appearance, Display, Users Accounts, etc. The only match for "screen" is for setting screen brightness.

Is there a gconf setting for this? Or a file setting that I can edit in emacs?

---

