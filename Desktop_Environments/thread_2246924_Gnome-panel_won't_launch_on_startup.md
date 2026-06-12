---
title: "Gnome-panel won't launch on startup"
date: 2014-10-04
forum: Desktop Environments
---

### Post by lunalui on 2014-10-04
Hi everybody,
I wonder whether you could help me with a recent issue I have. Over the last few days the gnome-panel won't load when I login on my ubuntu trusty (with gnome desktop). I added gnome-panel to my startup applications, but it doesn't load anyway. I've also tried what's suggested in this thread:
[http://askubuntu.com/questions/459551/gnome-flashback-panels-not-starting-in-ubuntu-14-04](http://askubuntu.com/questions/459551/gnome-flashback-panels-not-starting-in-ubuntu-14-04)
again with no success.


When I launch gnome-panel from a terminal I get this error message:

*** BUG ***
In pixman_region32_init_rect: Invalid rectangle passed
Set a breakpoint on '_pixman_log_error' to debug

any ideas what the problem can be? Thanks in advance for your help.

---

### Post by XDevHald on 2014-10-04
Hi lunalui,

Run the following commands to repair this issue.

**Step 1) Remove Gnome Panel**
```
sudo apt-get remove gnome-panel
```

**Step 2) Install Gnome Panel**
```
sudo apt-get install gnome-panel
```

---

### Post by lunalui on 2014-10-04
Hi XDevHald,
thanks for your reply and suggestion. Unfortunately removing and reinstalling did not fixed the problem, but you're right I should have tried that before posting and I should have remarked that I had done so in my post.

---

### Post by pissedoffdude on 2014-10-04
Isn't gnome-panel the top panel that Unity uses?  If you're using gnome as your DE, then gnome-shell is what's the problem.  So just to clarify, you're using gnome and your panels aren't loading, or what's going on?

Also, you can check if it's related to your current configuration by doing a
```
mv ~/.config ~/.config.bak
```

and relogging

---

### Post by lunalui on 2014-10-04
thanks for the tip: yeah, it works now but it completely erased my old configuration.

---

### Post by pissedoffdude on 2014-10-04
Alrighty.  You still have your old configuration, so we should figure out what it is.  If you're using gnome, check your extensions.  Did you update to 3.14? Could it be the case you have an incompatible extension?  It's always a pain when it's a user settings issue, but check as much as you can.  And if you want your old configuration back, just change the command I posted previously by interchanging the target and source directories.

---

### Post by CantankRus on 2014-10-04
You may want to confirm the session you're logging into...
```
echo $DESKTOP_SESSION
```

---

### Post by lunalui on 2014-10-05
> **pissedoffdude said:**
>   And if you want your old configuration back, just change the command I posted previously by interchanging the target and source directories.

that's the problem: I do not know how it happened or what happened but the old configuration I had moved to .bak has disappeared (don't ask!) so I'm reconfiguring everything right now!
In any case, it's hard to say where the problem was, because the panel had been working fine for quite some time. Also, it looks like I wasn't the only one with this problem:
[http://askubuntu.com/questions/471403/gnome-panel-crashed-and-now-wont-load-in-gnome-flashback-metacity-and-compiz](http://askubuntu.com/questions/471403/gnome-panel-crashed-and-now-wont-load-in-gnome-flashback-metacity-and-compiz)

---

### Post by lunalui on 2014-10-05
CantankRus, 
the session I'm logging in is
gnome-fallback (metacity)

---

### Post by CantankRus on 2014-10-05
I had a similar problem but couldn't work out how to only start in the fallback session
so wrote a script to check session and only start in the fallback session.
[http://ubuntuforums.org/showthread.php?t=2244135](http://ubuntuforums.org/showthread.php?t=2244135)

---

### Post by CantankRus on 2014-10-09
For another unrelated reason I set gnome-panel back to default with this command...
```
dconf reset -f /org/gnome/gnome-panel/
```
and it again loads at startup in the fallback session.

---

