---
title: "automatically starting program"
date: 2013-02-27
forum: Desktop Environments
---

### Post by madnbri on 2013-02-27
Hi,
evince starts automatically still I used it at first time, but I want to do not.
I tried to edit it from main menu -> Settings -> Session -> Automatically starting applications, but there is no evince. (The path is translated, so it may be different in English version of Xfce - I hope it is understandable.)

Where can I stop these applications in Xfce and where in command line?
Thanks in advance,
m

---

### Post by slickymaster on 2013-02-27
Start the **xfce4-autostart-editor** and remove the application(s).
You can also manually delete those files in **~/Desktop/Autostart** and **~/.config/autostart**.

Most of the time closing all the applications and saving your session when you logout is sufficient. If this doesn't work, remove the content of the **~/.cache/sessions/** folder when you're not logged in. And if you don't want xfce remember every session you should turn off (uncheck) “Automatically save session on logout” in **Settings Manager &#8594; Sessions and Startup** (tab General).

---

### Post by madnbri on 2013-02-27
> **slickymaster said:**
> Start the **xfce4-autostart-editor** and remove the application(s).
You can also manually delete those files in **~/Desktop/Autostart** and **~/.config/autostart**.There is no application like **xfce4-au*** in command line and package list and **~/Desktop/Autostart, ~/.config/autostart** are also missing.

> **slickymaster said:**
>  Most of the time closing all the applications and saving your session when you logout is sufficient. If this doesn't work, remove the content of the **~/.cache/sessions/** folder when you're not logged in. And if you don't want xfce remember every session you should turn off (uncheck) “Automatically save session on logout” in **Settings Manager &#8594; Sessions and Startup** (tab General).
I've checked before and set - same.

---

### Post by slickymaster on 2013-02-27
> **madnbri said:**
> There is no application like **xfce4-au*** in command line and package list and **~/Desktop/Autostart, ~/.config/autostart** are also missing.

Yes there is. See [this]("http://manned.org/xfce4-autostart-editor/a6f73395") and [this]("http://manpages.ubuntu.com/manpages/natty/man1/xfce4-autostart-editor.1.html").

---

### Post by madnbri on 2013-02-27
> **slickymaster said:**
> Yes there is. See [this]("http://manned.org/xfce4-autostart-editor/a6f73395") and [this]("http://manpages.ubuntu.com/manpages/natty/man1/xfce4-autostart-editor.1.html").
No, there isn't. See this:```
me@mycomp:~$ sudo apt-get install xfce4-autostart-editor
Reading package list… Ready0%
Building dependence tree       
Reading status information… Ready
E: This package cannot be found: xfce4-autostart-editor
```

---

### Post by slickymaster on 2013-02-27
You're right. Xfce4-autostart-editor has been integrated in **xfce4-session-settings** since Xfce 4.6.

---

### Post by Toz on 2013-02-27
> **slickymaster said:**
>  If this doesn't work, remove the content of the **~/.cache/sessions/** folder when you're not logged in.

Have you tried this? It sounds like evince is saved in the cached sessions.

---

### Post by slickymaster on 2013-02-27
> **Toz said:**
> Have you tried this? It sounds like evince is saved in the cached sessions.

Yes, I had a similar problem but with Chrome, every time I logged into my account, Chrome would automatically launch itself.

After a lot of fiddling with no success I come upon [Xfce wiki web page]("http://wiki.xfce.org/faq#session_manager") where they mention the fact that there are two possible reasons why applications are always started at login. Quoting:
> It is saved in the last session or it is listed in the auto started applications.

---

### Post by madnbri on 2013-02-27
> **Toz said:**
> Have you tried this? It sounds like evince is saved in the cached sessions.Yes, but these files don't exist. Where can I found session data?

---

### Post by slickymaster on 2013-02-27
> **madnbri said:**
> Yes, but these files don't exist. Where can I found session data?

The xfce4-session program starts up the Xfce Desktop Environment and is typically executed by your login manager. It will load your last session or a default session that includes the standard Xfce programs if no saved session is available.

xfce4-session uses the contents of the **~/.cache/sessions/** directory for starting previously saved sessions and reads its configuration from the file **$XDG_CONFIG_DIRS/xfce4-session/xfce4-session.rc**.

xfce4-session stores its session data into **$XDG_CACHE_HOME/sessions/**.

All the information is available in the [=session&s[]=data#files_and_environment_variables"]Xfce Docs]("http://docs.xfce.org/xfce/xfce4-session/advanced?s[).

---

### Post by madnbri on 2013-02-27
> **slickymaster said:**
> The xfce4-session program starts up the Xfce Desktop Environment and is typically executed by your login manager. It will load your last session or a default session that includes the standard Xfce programs if no saved session is available.

xfce4-session uses the contents of the **~/.cache/sessions/** directory for starting previously saved sessions and reads its configuration from the file **$XDG_CONFIG_DIRS/xfce4-session/xfce4-session.rc**.

xfce4-session stores its session data into **$XDG_CACHE_HOME/sessions/**.

All the information is available in the [=session&s[]=data#files_and_environment_variables"]Xfce Docs]("http://docs.xfce.org/xfce/xfce4-session/advanced?s[).Strange. Can I found an actual documentation somewhere? I show what I mean:```
z@x4tmp:~$ echo $XDG_CONFIG_DIRS
/etc/xdg/xdg-xubuntu:/etc/xdg:/etc/xdg
z@x4tmp:~$ echo $XDG_CACHE_HOME

z@x4tmp:~$ ls /etc/xdg/
autostart  Thunar          user-dirs.conf      xdg-xubuntu
menus      Trolltech.conf  user-dirs.defaults  xfce4
z@x4tmp:~$ ls /etc/xdg/autostart/
at-spi-dbus-bus.desktop                      print-applet.desktop
blueman.desktop                              pulseaudio.desktop
gnome-keyring-gpg.desktop                    pulseaudio-kde.desktop
gnome-keyring-pkcs11.desktop                 update-notifier.desktop
gnome-keyring-secrets.desktop                user-dirs-update-gtk.desktop
gnome-keyring-ssh.desktop                    xfce4-notes-autostart.desktop
gsettings-data-convert.desktop               xfce4-power-manager.desktop
nm-applet.desktop                            xfce4-volumed.desktop
onboard-autostart.desktop                    xfsettingsd.desktop
polkit-gnome-authentication-agent-1.desktop  xscreensaver.desktop
```File doesn't exist in this folder and as you can see $XDG_CACHE_HOME is not set.

---

### Post by Toz on 2013-02-27
What does the following return:
```
fgrep -r evince ~/.cache/sessions/*
```

---

### Post by madnbri on 2013-02-28
> **Toz said:**
> What does the following return:
```
fgrep -r evince ~/.cache/sessions/*
```Yess! This is the one. I post it:
```
~$ fgrep -r evince ~/.cache/sessions/*
...
Client7_CloneCommand=evince
Client7_DiscardCommand=/bin/rm,-rf,/home/z/.config/session-state/evince-1354915301.desktop
**Client7_RestartCommand=evince,--sm-client-id,2d635dc88-87e0-4351-b299-7c5e60348958,--sm-client-state-file,/home/z/.config/session-state/evince-1354915301.desktop**
Client7_DesktopFile=file:///usr/share/applications/evince.desktop
Client7_Program=evince
...
```These lines were in *~/.cache/session/xfce4-session-x4tmp\:0*. I made a (safe) copy of this file and deleted this (**bold**) line from original ~/.cache/sessions/xfce4-session-x4tmp\:0 where fgrep shown before.
I restarted and :D. It is solved.
Thanks for help.

---

