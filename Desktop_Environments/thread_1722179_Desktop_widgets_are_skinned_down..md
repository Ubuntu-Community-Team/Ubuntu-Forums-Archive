---
title: "Desktop widgets are skinned down."
date: 2011-04-05
forum: Desktop Environments
---

### Post by spitfirejunky on 2011-04-05
Occasionally when I start Ubuntu, all desktop widgets get skinned down.

This is what it looks like when it's normal:

[http://i.imgur.com/pcZMW.png](http://i.imgur.com/pcZMW.png)

This is what it looks like when something goes wrong:

[http://i.imgur.com/wrauR.png](http://i.imgur.com/wrauR.png)

The error only occurs at startup, and happens less often than not. It has been happening for a very long time, under two different machines and several kernels for the past 2 years to be exact.

I'm currently running 64-bit Ubuntu with linux-image-2.6.35-28-generic. Let me know if you need any more details about my setup or anything else.

---

### Post by Copper Bezel on 2011-04-05
It's an issue in 10.10. Restarting Gnome-Settings-Daemon and Nautilus fixes it, and you can create a startup script to do the same. See [here]("http://ubuntuforums.org/showthread.php?t=1575703").

---

### Post by spitfirejunky on 2011-04-05
I already use:

```
sudo /etc/init.d/gdm restart
```

I take it that there's no permanent solution?

I also couldn't find anything helpful in that thread.

---

### Post by Copper Bezel on 2011-04-05
Wow, doesn't that command kill the xserver? The same as logging out?

It's not a solid solution, but it is permanent in the sense that it's persistent. I know that thread's a bit difficult to navigate. What you want to do is this:

Go to Preferences -> Startup Applications.

Add. Enter

```
sleep 10s; gnome-settings-daemon && killall nautilus
```

Three parts in there: A delay, the settings daemon, and a restart of the file browser and desktop background, which is one app that the settings won't apply to unless it's loaded after the daemon runs.

Now it *should* never happen again. Your backdrop might flicker on login.

---

### Post by spitfirejunky on 2011-04-07
Thank you.

I adjusted the settings to do this. I'll reply to this thread if the problem resurfaces.

---

### Post by spitfirejunky on 2011-04-11
So after several restarts the problem has **not** resurfaced. Just thought I'd put that out there.

Once again, thanks.

---

### Post by Copper Bezel on 2011-04-11
Very cool - glad to hear it. = )

---

### Post by borobudur on 2011-06-05
> **Copper Bezel said:**
> 
Go to Preferences -> Startup Applications.

Add. Enter

```
sleep 10s; gnome-settings-daemon && killall nautilus
```

This works just in super user mode for me, so it doesnt in the startup applications :-(

---

### Post by Copper Bezel on 2011-06-05
Does [this]("http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html") fix work?

---

### Post by borobudur on 2011-06-07
> **Copper Bezel said:**
> Does [this]("http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html") fix work?

Unfortunatly this didn't fix it too. I also rised the sleep time but didn't help. 
I guess this also will be run in local user mode instead root.

---

### Post by Copper Bezel on 2011-06-07
Well, root shouldn't be running Gnome Settings Daemon at all. It's run by gdm in, well, GDM, then it's run by your user account in Gnome.

---

