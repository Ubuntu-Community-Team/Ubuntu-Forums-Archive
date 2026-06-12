---
title: "SERIOUS JAVA problem..."
date: 2006-08-23
forum: Desktop Environments
---

### Post by Efrain Valles on 2006-08-23
Dear all...

I am experiencing something strange... I started using automatix and through it Installed JRE and JDK... later on I downloaded eclipse... It ran fine for a while... but I tried to get the MYSQL plug-in for JSK... Not knowing If automtix had really installed JDK I 2ent ahead and installed JDK from repos... Now.. ECLIPSE won't load... :confused:  I  did something stupid .. but my question is ... is there a solucion...

Also every time I download upgrades I get this error

```
Setting up j2sdk1.4-doc (1.4.2.02-1ubuntu3)...
This package is an installer package, it does not actually contain J2SDK documentation. You will need to go download one of the archives:

     j2sdk-1_4_2-doc.zip j2sdk-1_4_0-doc-ja.zip j2sdk-1_4_2-doc-ja.zip

choose the non-update version if this is the first installation).
Please visit

     http://java.sun.com/j2se/1.4.2/download.html

now and download. the file should owned by root.root and be copied to /tmp.
[Press RETURN to try again, 'no' + RETURN to abort] no

```

I don't understand Please help...](*,) 

Efrain

---

### Post by Tomosaur on 2006-08-23
If Eclipse was working fine, then the JDK will have been installed correctly. I'm not familiar with what Automatix actually installs - there are several possibilites as to which JDK it decided to download. If you downloaded a different JDK to the one it used, it's possible that you may have conflicting paths and so Eclipse doesn't know which to use. Could you copy and paste the result of the following command (from the terminal)
```

printenv

```

---

### Post by Efrain Valles on 2006-08-23
I-ll give it a go when I get home...

gee thanks for your promt responce

---

### Post by Efrain Valles on 2006-08-23
Here is my printenv

```
valles@voices:~$ printenv
SSH_AGENT_PID=4889
TERM=xterm
DESKTOP_STARTUP_ID=
SHELL=/bin/bash
GTK_RC_FILES=/etc/gtk/gtkrc:/home/valles/.gtkrc-1.2-gnome2
WINDOWID=50331733
GTK_MODULES=gail:atk-bridge
USER=valles
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:
GNOME_KEYRING_SOCKET=/tmp/keyring-idABZM/socket
SSH_AUTH_SOCK=/tmp/ssh-GbTYrb4691/agent.4691
SESSION_MANAGER=local/voices:/tmp/.ICE-unix/4691
USERNAME=valles
DESKTOP_SESSION=default
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
GDM_XSERVER_LOCATION=local
PWD=/home/valles
LANG=en_AU.UTF-8
GDMSESSION=default
HISTCONTROL=ignoredups
HOME=/home/valles
SHLVL=1
LANGUAGE=en_AU:en
GNOME_DESKTOP_SESSION_ID=Default
LOGNAME=valles
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-R51e4H31fC,guid=420eed4431c697ac96521332289c1d00
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/home/valles/.Xauthority
_=/usr/bin/printenv

```

---

