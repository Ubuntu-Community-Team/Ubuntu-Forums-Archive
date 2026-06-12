---
title: "LXDE, pcmanfm crashing after update"
date: 2013-05-19
forum: Desktop Environments
---

### Post by temporos on 2013-05-19
I got the latest updates to both LXDE and pcmanfm, as well as a whole bunch of security updates and a couple kernel updates for Lubuntu 12.10. Now, odd things are happening.

When I highlight a file in pcmanfm and hit the "alternate menu" button (the one on the right side of the space bar between the Windows and Ctl keys), the menu that appears lists the options as if nothing is highlighted. I frequently use the keyboard to bring up right-click options, so this is very inconvenient. A right-click itself seems to work normally.

Also, no file on the desktop can be accessed from the desktop. If I right-click the desktop or any files on it, both pcmanfm and LDXE crash. If I try to open a file on the desktop by either double-clicking it or highlighting it and pressing Enter, both pcmanfm and LXDE crash. I can move files from the desktop to another folder and access them, but accessing anything on the desktop will cause a crash.

Finally (so far), the "Shutdown" panel icon and the "Logout" menu item have both stopped working. Clicking them does nothing anymore, where they used to bring up a menu giving me the option to log out, shutdown, restart, etc.. Now to shutdown, I have to bring up a terminal and run a *shutdown*&#8203; command directly.

Has anyone else had these issues since the latest updates, and if so, how did you fix them?

---

### Post by ibjsb4 on 2013-05-20
First thing I always blame is the kernel :)  Try backing up to previous kernel.

---

### Post by temporos on 2013-05-20
I suspect that it's the kernel update, too. A couple questions first, though.

How did a kernel update with such a visible and regressive flaw make it into the release cycle?

The Lubuntu update manager says that I can upgrade to Lubuntu 13.04. Should I consider this instead of restoring a previous kernel?

What do you make of this (I found it rather interesting)? This is the *exec* command run by the "shutdown" panel application and the "logout" menu item.
```
user@localhost:~$ lubuntu-logout
/usr/bin/lubuntu-logout: 2: /usr/bin/lubuntu-logout: lxsession-logout: not found
```
The logout command is just... *gone*&#8203;?

---

### Post by RockDoctor on 2013-05-21
FWIW, I'm running Lubuntu 13.04 and just looked - no lxsession-logout, and:
```
~$ cat /usr/bin/lubuntu-logout 
#!/bin/sh
lxsession-logout --banner "/usr/share/lubuntu/images/logout-banner.png" --side=top

```

---

### Post by vasa1 on 2013-05-21
> **RockDoctor said:**
> FWIW, I'm running Lubuntu 13.04 and just looked - no lxsession-logout, and:
```
~$ cat /usr/bin/lubuntu-logout 
#!/bin/sh
lxsession-logout --banner "/usr/share/lubuntu/images/logout-banner.png" --side=top

```
See the same contents as you do. Lubuntu 13.04. Fully updated. No problems with logging out.

Although PCManFM didn't crash on me, I saw the same problem as OP regarding the "alternate menu" behaving a bit oddly. In addition, there's a known issue with drag and drop: [https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1179167](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1179167) with a small YouTube video to illustrate it: [http://youtu.be/ix6P6ZwQR-k](http://youtu.be/ix6P6ZwQR-k)

Long story cut short, I've replaced PCManFM both as file manager and for handling the desktop with Thunar and xfdesktop.

---

### Post by temporos on 2013-05-21
I'm thinking a recent kernel upgrade FUBAR'd my install. :-| I've noticed several other things that no longer work while they still should (and claim to). I'll probably reformat and do a clean install of 13.04 tonight.

vasa1, do you need to use **both** Thunar and xfdesktop to replace pcmanfm? I kind of liked the pcmanfm that came installed with Lubuntu through 12.04. It was only after upgrading to 12.10 that I started to have issues.

---

### Post by RockDoctor on 2013-05-21
As a work-around, I tried copying lxsession-logout from my Fedora 19 install to /usr/local/bin. Seems to work

---

### Post by vasa1 on 2013-05-21
> **temporos said:**
> ...
vasa1, do you need to use **both** Thunar and xfdesktop to replace pcmanfm? ....
In case you are still interested, please look at:
[LXDE/XFCE Hybrid]("http://askubuntu.com/a/73101/25656") and a bit more here:
[Why is pcmanfm is still running after following the LXDE/XFCE Hybrid instructions?]("http://askubuntu.com/q/285935/25656")

---

### Post by vasa1 on 2013-05-21
> **RockDoctor said:**
> As a work-around, I tried copying lxsession-logout from my Fedora 19 install to /usr/local/bin. Seems to work
Hi, what is your problem with logging out? What is not working? Do you have problems with logging out via the GUI or logging out via the terminal?

I have no difficulty with logging out or shutting down via the GUI. I haven't tried the terminal approach.

---

### Post by pcgaldo on 2013-05-22
For alternate menu key issue, we've notified it in [Launchpad]("https://bugs.launchpad.net/pcmanfm/+bug/1183126") and [PCManFM Sourceforge bug tracker]("https://sourceforge.net/tracker/?func=detail&aid=3613751&group_id=156956&atid=801864").

You can subscribe it and notify a "also affects me" in Launchpad.

---

### Post by vasa1 on 2013-05-22
> **pcgaldo said:**
> For alternate menu key issue, we've notified it in [Launchpad]("https://bugs.launchpad.net/pcmanfm/+bug/1183126") and [PCManFM Sourceforge bug tracker]("https://sourceforge.net/tracker/?func=detail&aid=3613751&group_id=156956&atid=801864").

You can subscribe it and notify a "also affects me" in Launchpad.
Thanks! "Me too"ed it.

---

### Post by temporos on 2013-05-23
I never got the chance to do that. :-? Shortly after my last post, everything started breaking. Processes started failing all over the place, and eventually, the system itself failed to boot properly. I ended up simply doing a complete format and reinstall using the 13.04 live image. Something really bad must have happened in one of the 12.10 security or kernel updates.

Short version - a reformat and clean install of Lubuntu 13.04 fixed all the problems except the two non-critical pcmanfm bugs that are already known (the desktop drag and right-click menu issues).

---

### Post by temporos on 2013-05-23
> **pcgaldo said:**
> You can subscribe it and notify a "also affects me" in Launchpad.
This is going to sound dumb, but...

How do I log in to Launchpad using my OpenID? I don't want another OpenID by registering a new account.

---

