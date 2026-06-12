---
title: "lightdm failed to find session configuration ubuntu"
date: 2014-05-26
forum: Desktop Environments
---

### Post by maclenin on 2014-05-26
**ISSUE:**

I cannot get past the login screen, either as "user" or "guest" when attempting to start-up ubuntu 13.10.

Essentially, after laptop (HP-Compaq 2510p) power-up, the lightdm page / login prompt is presented. Once the password is entered (i.e. no autologin), the password entry field clears and there is no progress to the desktop page / ubuntu session. Shutdown, clock, sound, language and network manager icons all appear on the upper right of the lightdm login page and seem to function properly. The computer name appears on the upper left. 

I am able to toggle between a terminal session (ctrl+alt+f1) and lightdm login page (ctrl+alt+f7), however, I am not able to launch any graphical applications - such as thunar, firefox, leafpad, etc from the terminal.... For example, when trying to launch thunar via the terminal, it shows:
```
Thunar: Cannot open display:
```
**NOTES:**

1. I had been working to re-install **libimobiledevice** - just prior to experiencing this problem. I had installed libimobiledevice-1.1.6 and THEN completed **removal** of an older version of **libimobiledevice** and related items (**gvfs-backends, libgpod-common, libgpod4, upower**)  via the software-center. Perhaps, there is some connection between the libimobiledevice removal and the larger issue?

2. A, perhaps, relevant snippet from **/var/log/lightdm/lightdm.log** shows:
```
[x] DEBUG: Session pid=y: Authentication complete with return value 0: Success
[x] DEBUG: Session pid=y: Authenticate result for user **z**: Success
[x] DEBUG: Session pid=y: User **z** authorized
[x] DEBUG: Session pid=y: Greeter requests session ubuntu
[x] DEBUG: Writing **/home/[B]z**/.dmrc[/B]
[x] DEBUG: Seat: **Failed to find session configuration ubuntu**
[x] DEBUG: Seat: Can't find session 'ubuntu'
```
2.a. A **cat /home/z/.dmrc** shows:
```
[Desktop]
Session=ubuntu
```
3. All had been working well up until restart **immediately after** removal of the old **libimobiledevice**.

Thanks for any guidance!

---

### Post by steeldriver on 2014-05-26
What are the contents of your /usr/share/xsessions directory? does it contain a ubuntu.desktop session file?

---

### Post by maclenin on 2014-05-26
**steeldriver!**

Thanks for the reply.

The only quasi-reference I have to **xsessions** - as determined via locate is: /etc/upstart-xsessions
The only quasi-reference I have to **ubuntu.desktop** - as determined via locate is: /usr/share/app-install/desktop/edubuntu.desktop

Thoughts?

---

### Post by steeldriver on 2014-05-26
Hmm... what about

```

dpkg -l gnome-session

```

It's starting to sound like it got uninstalled somehow

---

### Post by maclenin on 2014-05-26
Running **dpkg -l gnome-session** shows, essentially:
```
<none> and (no description available)
```
The desktop environment that's failing was whatever the default 13.10 ubuntu install environment is - is it unity?

When I run **unity** from the command line, I get:
```
WARNING: no DISPLAY variable set, setting it to :0
compiz (core) - Info: Loading plugin: core
unity-panel-service: no process found
compiz (core) - Info: Starting plugin: core
Invalid MIT-MAGIC-COOKIE-1 keycompiz (core) - Fatal: Couldn't open display :0
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core
```
Do you think those applications removed along with **libimobiledevice** could have played a role?

Thanks, again, for the suggestions.

---

### Post by steeldriver on 2014-05-26
I would suspect that removal of gvfs-backends is the culprit - consider

```

$ apt-cache rdepends --recurse gvfs-backends | grep gnome-session
  gnome-session-flashback
  gnome-session-flashback
  gnome-session
  .
  .
  .

```

You could *try*

```

sudo apt-get install --reinstall gnome-session

```

or perhaps even

```

sudo apt-get install --reinstall ubuntu-desktop

```

although tbh if ubuntu-desktop was removed I'm kind of surprised you still have a GUI (lightdm?) login screen

---

### Post by maclenin on 2014-05-26
Bingo!

Thanks, **steeldriver**, the install --reinstall of **gnome-session** / gvfs-backends was the ticket, it seems. I had, actually, considered that **gvfs-backends** might be involved but hadn't the ken to run **apt-cache rdepends --recurse gvfs-backends | grep gnome-session** to test my therory....

Which, begs the question, for a separate thread, perhaps - when preparing to install a new version of libimobiledevice, shouldn't one (be able to) remove the old version, first? I didn't know that libimobiledevice (and dependecies) were (so) hardwired into the fabric of the desktop....

Thanks, again!

---

