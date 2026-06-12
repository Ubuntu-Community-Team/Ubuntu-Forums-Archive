---
title: "How to use Lightdm login manager instead of gdm"
date: 2010-11-10
forum: Desktop Environments
---

### Post by Crazedpsyc on 2010-11-10
I just installed Lightdm from "bob"'s ppa, and it looks great when I run it from a virtual console (like Ctrl+Alt+F5), but how can I replace the gdm login manager with it? And when I do that how can I make ldm not register the Samba Guest User as an actual user?

I am using ubuntu 10.10

---

### Post by Crazedpsyc on 2010-11-11
I assumed this would be  a simple question sorry. Hasn't anyone done this before?

---

### Post by Crazedpsyc on 2010-11-12
Nobody? Really? Well I'll see if bob can help and post what he has to say here.

---

### Post by hellnest on 2010-11-12
> **Crazedpsyc said:**
> Nobody? Really? Well I'll see if bob can help and post what he has to say here.

It's quite easy,

1. uninstall GDM
2. Install LightDM
3. Reboot

( For a good shake try uninstall and install the application through aptitude in command line )
```
sudo bash
```
Enter your password here
```
aptitude
```

---

### Post by Crazedpsyc on 2010-11-13
Thanks for the try, bob didn't help. I ran ```
sudo apt-get remove gdm && sudo apt-get install lightdm
```
but when I restarted I got an error saying "Ubuntu is running in low graphics mode." and it gave me options to restart x, exit to console, reconfigure graphics, and run in low graphics mode for one session.
when I tried the run in low graphics mode, it just sat at a black screen. Oh, and the cursor during that time was the big X 'X'. This is no real loss since I have been using the recovery console for the past month instead of GDM, but I still want to have lightdm.
If I run "sudo lightdm" from the recovery console I get a black screen and the only way to get away is to press the physical off button. 
If I run "lightdm --test-mode" from a terminal (after startx from the console) it says:
```
** (process:4390): WARNING **: Greeter failed
```
But *that* worked before, so I don't know why it fails now unless there was an update overnight or this morning that broke it.
I will try apt-get clean and then reinstall it now.

---

### Post by Crazedpsyc on 2010-11-15
bump

---

### Post by Crazedpsyc on 2010-11-16
Any other ideas hellnest?

---

### Post by Crazedpsyc on 2010-11-17
bump

---

### Post by Crazedpsyc on 2010-11-18
bump

---

### Post by Crazedpsyc on 2010-11-22
BuMp again. I don't much like using ubuntu without a login screen. I have to use the recovery console to log in.

---

### Post by Crazedpsyc on 2010-11-24
I got gdm to work again by apt-get purging it and then reinstalling it. then i tried one more time just uninstalling it, installing lightdm (I purged it first too) and rebooting, but I got the same Low Graphics Mode error. It does work in test-mode now, but I want to use it in real mode!

---

### Post by Crazedpsyc on 2010-11-29
Purged lightdm and gdm again, then sudo rm-ed everything that came up in locate lightdm and apt-get cleaned before finally installing lightdm again and rebooting. I still got the same problem.

---

### Post by Crazedpsyc on 2010-12-01
bump

---

### Post by Crazedpsyc on 2010-12-02
buump

---

### Post by 1forthedoctor on 2010-12-03
if reinstalling doesn't help the first time around it probably won't the second time either...

anyways, i've got lightdm up and running here, problem was a missing dbus file. i am sure the permissions could be wrapped tighter and lightdm is also still running as root.

/etc/dbus-1/lightdm.conf:
```
<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>

  <!-- Only root can own the service -->
  <policy user="root">
    <allow own="org.lightdm.LightDisplayManager"/>
  </policy>

  <!-- Limit access to greeter API -->
  <policy user="root">
    <allow send_destination="org.lightdm.LightDisplayManager" send_interface="org.lightdm.LightDisplayManager.Greeter"/>
  </policy>
  <policy user="@GREETER_USER@">
    <allow send_destination="org.lightdm.LightDisplayManager" send_interface="org.lightdm.LightDisplayManager.Greeter"/>
  </policy>

  <policy context="default">
    <allow send_destination="org.lightdm.LightDisplayManager" send_interface="org.freedesktop.DBus.Properties"/>
    <allow send_destination="org.lightdm.LightDisplayManager" send_interface="org.freedesktop.DBus.Introspectable"/>
    <allow send_destination="org.lightdm.LightDisplayManager" send_interface="org.lightdm.LightDisplayManager"/>
    <allow send_destination="org.lightdm.LightDisplayManager" send_interface="org.lightdm.LightDisplayManager.Display"/>
    <allow send_destination="org.lightdm.LightDisplayManager" send_interface="org.lightdm.LightDisplayManager.Users"/>
    <allow send_destination="org.lightdm.LightDisplayManager" send_interface="org.lightdm.LightDisplayManager.Session"/>
  </policy>

</busconfig>
```

next thing to do is edit **/etc/init/gdm.conf** and add an exec line for lightdm:

```
#exec gdm-binary $CONFIG_FILE
exec /usr/bin/lightdm -c /etc/lightdm.conf
```

/etc/lightdm.conf:
```
[LightDM]
xserver=/usr/bin/X
log-directory=/var/log/lightdm
session-wrapper=/etc/X11/Xsession
displays=default-display

[default-display]
greeter-theme=gnome
greeter-user=gdm

```

---

### Post by Crazedpsyc on 2010-12-06
Thanks! I did all that and will restart asap!


Uh oh, I got the same error!

---

### Post by Crazedpsyc on 2010-12-09
I am downloading the latest lightdm right now, so I'll se if that fixes it :/
The screen went black, all the virtual consoles froze, and I had to reboot.
I think it might have something to do with my bad choice to keep the old lightdm.conf, so I'll try to either reinstall lightdm or manually download in move the new file to /etc/lightdm/

---

### Post by Crazedpsyc on 2010-12-14
Well, I got it to work, but then I uninstalled it and put gdm back when I noticed that the keymap was somehow messed up. After rebooting this fixed it, but of course then I had gdm.
Here's the problem I had:
Whenever I pushed the up arrow, it took a screenshot! as a gamer and terminal user, the up arrow is quite important to have ;)

---

### Post by Crazedpsyc on 2011-05-02
I just installed lightdm again in natty, and the problem is still there. 
Up, Down, Right, and End keys don't function properly.

---

### Post by BrokenKingpin on 2011-05-02
I have no idea how to fix your current issue, but have you considered try SLiM (Simple Login Manager)? Easy to setup and use, and has very few decencies.

---

### Post by Bremm on 2011-05-09
Try to use **greeter-user=root** at **/etc/lightdm.conf**

I already tried with *lightdm* and *gdm* users, but no way. I know *root* is insecure for this, but it's better than *suid* the greeter.

---

### Post by Sealbhach on 2011-05-12
I was going to experiment with lightdm but I think I'll stay away from it after reading this thread. :o

I just heard that it's going to be in the next Ubuntu release.

---

