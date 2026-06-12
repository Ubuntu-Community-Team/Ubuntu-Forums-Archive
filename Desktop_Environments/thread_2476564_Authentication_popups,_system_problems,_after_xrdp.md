---
title: "Authentication popups, system problems, after xrdp installation on Ubuntu 20.04"
date: 2022-06-29
forum: Desktop Environments
---

### Post by milesthemeerkat on 2022-06-29
Hi all, I'm hoping to get some help with issues I've had on my Ubuntu 20.04 desktop machine following the installation of **xrdp**.

I originally installed **xrdp** via **apt** on the command line, and I have since uninstalled it the same way. I was attempting to get remote access working, but gave up on that and just want to go back now.

Ever since installing it, I get many popups requesting authentication which I did not used to. After logging in, I get multiple popups to authenticate to:
[LIST]
[*]refresh system repositories 
[*]create a color profile 
[*]create a color managed device 
[/LIST]

I attempted to fix this by following some instructions from blog posts I googled, which led me to do the following:

1. Add a file, /etc/polkit-1/localauthority/50-local.d/46-allow-update-repo.pkla with the contents:
```
[COLOR=#333333][FONT=Consolas]
[Allow Package Management all Users][/FONT][/COLOR][COLOR=#333333][FONT=Consolas]
Identity=unix-user:*[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]
Action=org.freedesktop.packagekit.system-sources-refresh[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]
ResultAny=yes[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]
ResultInactive=yes[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]
ResultActive=yes[/FONT][/COLOR] 

```

2. Add a file, /etc/polkit-1/localauthority/50-local.d/45-allow-colord.pkla with the contents:
```
[FONT=Courier New][COLOR=#333333][FONT=Consolas]
[Allow Colord all Users][/FONT][/COLOR][/FONT][FONT=Courier New][COLOR=#333333][FONT=Consolas]
Identity=unix-user:*[/FONT][/COLOR][/FONT][FONT=Courier New][COLOR=#333333][FONT=Consolas]
Action=org.freedesktop.color-manager.create-device;org.freedesktop.color-manager.create-profile;org.freedesktop.color-manager.delete-device;org.freedesktop.color-manager.delete-profile;org.freedesktop.color-manager.modify-device;org.freedesktop.color-manager.modify-profile[/FONT][/COLOR][/FONT][FONT=Courier New][COLOR=#333333][FONT=Consolas]
ResultAny=no[/FONT][/COLOR][/FONT][FONT=Courier New][COLOR=#333333][FONT=Consolas]
ResultInactive=no[/FONT][/COLOR][/FONT][FONT=Courier New][COLOR=#333333][FONT=Consolas]
ResultActive=yes[/FONT][/COLOR][/FONT] 

```
3. Add a file, /etc/polkit-1/localauthority.conf.d/02-allow-colord.conf with the contents:
```
polkit.addRule(function(action, subject) {
 if ((action.id == "org.freedesktop.color-manager.create-device" ||
 action.id == "org.freedesktop.color-manager.create-profile" ||
 action.id == "org.freedesktop.color-manager.delete-device" ||
 action.id == "org.freedesktop.color-manager.delete-profile" ||
 action.id == "org.freedesktop.color-manager.modify-device" ||
 action.id == "org.freedesktop.color-manager.modify-profile") &&
 subject.isInGroup("{users}")) {
 return polkit.Result.YES;
 }
 });
```

While following these steps did indeed get rid of the authentication popups, it causes other issues. I can no longer shutdown the machine in the typical way, via 'Power Off' -> 'Power Off' -> 'Shut down'. Tailing my **/var/log/syslog** when attempting, it outputs the following:
```
Jun 29 14:24:06 miles-ubuntu gnome-shell[1918]: endSessionDialog: No XDG_SESSION_ID, fetched from logind: NaN
Jun 29 14:24:09 miles-ubuntu systemd[1]: polkit.service: Main process exited, code=dumped, status=11/SEGV
Jun 29 14:24:09 miles-ubuntu systemd[1]: polkit.service: Failed with result 'core-dump'.
Jun 29 14:24:09 miles-ubuntu gnome-session[1904]: gnome-session-binary[1904]: WARNING: Shutdown failed: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Jun 29 14:24:09 miles-ubuntu gnome-session-binary[1904]: WARNING: Shutdown failed: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Jun 29 14:24:09 miles-ubuntu gnome-session-binary[1904]: Entering running state
Jun 29 14:24:09 miles-ubuntu gnome-shell[1918]: Ignored exception from dbus method: Gio.IOErrorEnum: GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dio_2derror_2dquark.Code19: Operation was cancelled
```

However, I can still manually shutdown if I do **sudo shutdown now **in the terminal.

I've since removed the files I described in steps 1~3, which allows me to shut down again, but of course, the authentication popups return.

Finally, I also get a system problem popup upon login now. When I look at the crash details, it is related to policykit. Here is a screenshot of some of the details:
[https://i.imgur.com/ajhRPZd.png](https://i.imgur.com/ajhRPZd.png)

Finally, I've also noticed that when I go to Power Off my machine now, it says there is another user logged in (but appears to be listing myself, the only user).

Any pointers for resolving these issues, or some information on what might have gone wrong?

---

### Post by ActionParsnip on 2022-06-30
What are you doing on the remote system that needs the remote desktop session? There may be a sleeker solution to what you want to achieve

---

### Post by milesthemeerkat on 2022-07-05
> **ActionParsnip said:**
> What are you doing on the remote system that needs the remote desktop session? There may be a sleeker solution to what you want to achieve

I don't even want to do that anymore and just want to be rid of the annoying popups for my password.

I was attempting to setup a remote session for doing development (web development and android development).

---

### Post by ActionParsnip on 2022-07-05
Do you use autologin? If so, then that can be why

---

### Post by milesthemeerkat on 2022-07-05
> **ActionParsnip said:**
> Do you use autologin? If so, then that can be why

No, I do not. I manually log in every time.

---

### Post by milesthemeerkat on 2022-07-18
I found an answer on AskUbuntu which resolved these problems. If anyone else encounters this issue, follow these steps by Ace.C: [https://askubuntu.com/a/1373856/1613837](https://askubuntu.com/a/1373856/1613837)

---

