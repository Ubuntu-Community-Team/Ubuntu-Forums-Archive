---
title: "From GNOME to XFCE"
date: 2011-03-07
forum: Desktop Environments
---

### Post by uqbar on 2011-03-07
I've (finally!) switched from GNOME to XFCE.
I did so by installing xubuntu-desktop and a few other xfce-related packages on top of my working (GNOME) Ubuntu desktop 10.10.

It's looks quite close to what I was looking for for everyday usage. Finally!

Two questions: I sill see a number of GNOME related processes running. Namely:
[LIST]
[*]gnome-power-manager
[*]gnome-keyring-daemon
[*]polkit-gnome-authentication-agent-1
[*]gnome-pty-helper
[/LIST]despite I've asked not to start GNOME services at boot.
So my question is: is this correct?
If not, how can I "fix" it?
Many thanks.

---

### Post by rvchari on 2011-03-07
> **uqbar said:**
> I've (finally!) switched from GNOME to XFCE.
I did so by installing xubuntu-desktop and a few other xfce-related packages on top of my working (GNOME) Ubuntu desktop 10.10.

It's looks quite close to what I was looking for for everyday usage. Finally!

Two questions: I sill see a number of GNOME related processes running. Namely:
[LIST]
[*]gnome-power-manager
[*]gnome-keyring-daemon
[*]polkit-gnome-authentication-agent-1
[*]gnome-pty-helper
[/LIST]despite I've asked not to start GNOME services at boot.
So my question is: is this correct?
If not, how can I "fix" it?
Many thanks.

you can delete them from the start up apps. it should be listed or checked, uncheck them or delte them from start up apps.


by the way i wish to know if multile windows can be open and visible in xfce. i had switched long back, now i am back to gnome coz i cant keep multiple windows visible. at the same time.

---

### Post by 3Miro on 2011-03-07
While XFCE is smaller and faster than Gnome, it is missing a few features. Adding a few Gnome services to XFCE is a common practice (especially among the Gnome-centric distributions like Ubuntu).

If you have a desktop computer, you can stop the power manager. If you have a laptop, you should try to replace Gnome-Power-Manager with XFCE-Power-Manager, which has less features (at the end you need a power manager).

The Keyring is actually important to keep track of wireless passwords and such. If you are using a wireless connection, then you should keep it running.

The other two processes I am not familiar with. You can turn them off to see what would break.

rvchari: what do you mean by multiple windows open and visible. I can have as many programs on as many workspaces as I want.

---

### Post by rvchari on 2011-03-07
> **3Miro said:**
> While XFCE is smaller and faster than Gnome, it is missing a few features. Adding a few Gnome services to XFCE is a common practice (especially among the Gnome-centric distributions like Ubuntu).

If you have a desktop computer, you can stop the power manager. If you have a laptop, you should try to replace Gnome-Power-Manager with XFCE-Power-Manager, which has less features (at the end you need a power manager).

The Keyring is actually important to keep track of wireless passwords and such. If you are using a wireless connection, then you should keep it running.

The other two processes I am not familiar with. You can turn them off to see what would break.

rvchari: what do you mean by multiple windows open and visible. I can have as many programs on as many workspaces as I want.

if one active window is open, other window seem to hide in desktop. only one window which is active seems to be visible on xfce desktop, have to randomly click on desktop to access other open windows !hope u got my point

---

### Post by 3Miro on 2011-03-07
> **rvchari said:**
> if one active window is open, other window seem to hide in desktop. only one window which is active seems to be visible on xfce desktop, have to randomly click on desktop to access other open windows !hope u got my point

There is a problem with your XFCE install or driver install or something else of that sort.

One thing that you can try is to go into XFCE, the press Alt+F2 and then type:
```
xfwm4 --replace
```

If this doesn't work, you can stat a support-request thread.

---

