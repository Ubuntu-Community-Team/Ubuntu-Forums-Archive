---
title: "&quot;session only lasted ten seconds&quot; message"
date: 2007-06-11
forum: Desktop Environments
---

### Post by mattalves on 2007-06-11
hello people,

all of a sudden i started getting a "session only lasted ten seconds" dialog while using gnome on feisty.

this is the error i get:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mateus"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/mateus-laptop:/tmp/.ICE-unix/8298
Aviso do gerenciador de janelas: "" localizado no banco de dados de configurações não é um valor válido para a tecla de atalho "toggle_shaded"
Initializing gnome-mount extension

(gnome-power-manager:8365): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(nm-applet:8363): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(eog:8376): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-cups-icon:8364): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(update-notifier:8368): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
```

any idea what it might be?

cheers and thanks in advance for the help

---

### Post by mattalves on 2007-06-11
one additional piece of info: I'm able to log in a failsafe gnome session and everything seems pretty normal. Also, i'm able to use everything in gnome (except session settings) while keeping the dialog open when in a normal session.

---

### Post by GrumpyBob on 2007-06-13
This happened to me once before and it turned out to be an issue to do with the hidden file .ICEauthority.  If you rename it from a failsafe or console login, you may find you are able to login again.  I think a new .ICEauthority is generated.

[edit - I should have said, .ICEauthority is in your home folder.]

Robert

---

### Post by joelio on 2007-06-13
This has no effect for me. I've tried it with another user as well.

I can sometimes get into the failsafe gnome session, but not all the time.. 

I did an apt-get update && apt-get upgrade today. (been working fine since installation! - serves me right to trust updates from Ubuntu!)

I'm also running Beryl.

What the hell is going on? Deleting the /tmp/* stuff makes no difference. I think this is a bug!!

---

### Post by joelio on 2007-06-13
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "joel"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/joel-desktop:/tmp/.ICE-unix/11132
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

(gnome-panel:11197): GnomeUI-WARNING **: While connecting to session manager:
IO error occured doing Protocol Setup on connection.

```

Is what I get

---

### Post by abc123456 on 2007-06-16
When that has happened to me I mv .bashrc to bashrc then reboot X.:popcorn:

---

