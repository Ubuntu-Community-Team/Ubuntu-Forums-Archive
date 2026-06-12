---
title: "Odd changes in Xfce today"
date: 2012-08-19
forum: Desktop Environments
---

### Post by Buntu Bunny on 2012-08-19
This morning when I opened my desktop (Xfce) I noted some odd changes:

- the home folder on the desktop is now partially hidden by top panel 1
- only 1 workspace. Even though my workspace settings are set to 4, the workspace changer only shows 1. If I change the number of workspaces in preferences, I still only get 1 workspace.
- no min/max/close buttons on windows except Google Chrome. However, min & max buttons don't work for it.
- some windows can't be dragged, eg weather app window, Settings Manager, & LibreOffice windows
- panel 1 no longer shows open windows
- Window Manager in Settings Manager is now blank. I'm guessing this has something to do with my problem(?) Could it have become corrupted somehow? It's not something I messed with because I was happy with the way things were. Can I restore it? Or is the source of the problem something else?

---

### Post by Buntu Bunny on 2012-08-19
Well, I've been doing some research on this and apparently it's not that uncommon of a problem. 

I found three similar bug reports at launchpad:
[https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/794551](https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/794551)
[https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/495361](https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/495361)
[https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/978333](https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/978333)

Also one at the Xfce forum: [http://forum.xfce.org/viewtopic.php?id=7382](http://forum.xfce.org/viewtopic.php?id=7382)

The workaround appears to be manually installing windows manager via terminal

```
xfwm4 --replace
```

But terminal won't run for me in Xfce either, it just comes up as a greyed out screen that won't respond to the keyboard. 

Anyway, that's what I've come up with so far. Still looking for answers!

---

### Post by Bucky Ball on 2012-08-19
Reboot, choose the recovery kernel. This will take you to a set of options. Drop to a shell as root with networking and try that command again. Exit and you will get back to the options. Choose 'Normal Boot'.

---

### Post by Buntu Bunny on 2012-08-19
Bucky Ball, thanks. When I switched back to Xfce from Gnome, terminal was responsive again. Apparently this bug is pretty quirky. The best news is that I got a fix via the Xfce Forum - 

> 
1. In a terminal, enter
```
xfwm4 --sm-client-disable
```
This should restore the desktop and the workspace switcher in the panel. If it doesn't...??

2. Open the run dialog with Alt+F2, and enter ```
xfwm4 --replace
```
This should restart xfwm4 properly.

3. Make sure everything in your session is set up as you prefer, then log out with 'save session on exit'.

4. Log in again. 

This worked and restored my desktop. What a relief. I really, really like Xfce and couldn't bear to think of having to give it up.

---

### Post by Bucky Ball on 2012-08-19
Love xfce. Don't use anything else. Started with xfce4 DE on regular Ubuntu but now I just use Xubuntu. ;)

PS: Cute avatar, BTW!

---

### Post by Buntu Bunny on 2012-08-19
I hadn't considered just using Xubuntu. It installed alongside Precise when I added Xfce. I'm a total Xfce convert. Maybe I need to learn more about Xubuntu too.

---

### Post by Bucky Ball on 2012-08-19
It's lighter, more pared back. All the *buntus use the same base and the rest - apps, DE, etc - are added to that. So much in Ubuntu I just don't use and after five years I know what my favourite apps are. I only want/need them and I can add other stuff if the need arises later.

Xubuntu fast and sleek without the fat. Minimal install good, too, but more involved. You add only what you want to the base when you're installing (including your choice of DE). End up with the proverbial rocket machine! I was getting to the login screen in 12 seconds on the last minimal install I did. ;)

---

