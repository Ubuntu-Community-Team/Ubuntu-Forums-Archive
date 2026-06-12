---
title: "Lost my Alt + F2 key to run a command."
date: 2011-06-01
forum: Desktop Environments
---

### Post by irv on 2011-06-01
I have been installing and un-installing apts, and I lost the ability to use the Atl + F2 key to run commands. Does anyone have an idea on how to fix this?
Thanks.

---

### Post by hhh on 2011-06-01
You should be able to fix this by going to Settings>>Xfce 4 Settings Manager>>Keyboard>>Application Shortcuts and add a new command called xfrun4 with the shortcut command of your choice.

---

### Post by irv on 2011-06-01
> **hhh said:**
> You should be able to fix this by going to Settings>>Xfce 4 Settings Manager>>Keyboard>>Application Shortcuts and add a new command called xfrun4 with the shortcut command of your choice.

[ATTACH]193882[/ATTACH]
As you can see it is already set.
I got it to work, but it was funky. If I hit the Ctrl+Alt+F2 it takes me to a command prompt, I then hit Ctrl+Alt+F7 to come back to the GUI and then the Alt + F2 will work. Go figure.
Thanks for the reply.

---

### Post by Sopalajo de Arrierez on 2011-12-26
Same problem here :-( .
   I have checked several posts and forums, but nothing gave me the solution.

---

### Post by neu5eeCh on 2011-12-26
I don't know how OCD you are about things working the way they're 'supposed' to work, but you could always install Synapse and map it to Alt+F2. Synpase allows you to run commands. Gets you the same thing, I think.

---

### Post by Toz on 2011-12-26
**xfce4-settings-helper** needs to be running for Alt-F2 to work in xfce/xubuntu.

---

### Post by neu5eeCh on 2011-12-26
Damn Toz. [Insert praise of choice.] How do you know this stuff? Did you build Linux from Scratch at some point? Are you a coder or developer? Do you have dependency trees built into your brain? Seems like, no matter how arcane, you're like the Linux Jeopardy Master.

---

### Post by Toz on 2011-12-26
> **VTPoet said:**
> Damn Toz. [Insert praise of choice.] How do you know this stuff? Did you build Linux from Scratch at some point? Are you a coder or developer? Do you have dependency trees built into your brain? Seems like, no matter how arcane, you're like the Linux Jeopardy Master.

lol. Maybe too much time on my hands? I've been using xfce for a number of years now and have experienced many of these problems myself.

---

### Post by neu5eeCh on 2011-12-26
Well, I know who to look for when Xubuntu 12.04 is released. I'm still using Xubuntu 11.04 and will wait. I hear the desktop will be managed by Thunar in the next release. That will be a welcome development.

---

### Post by Sopalajo de Arrierez on 2011-12-26
> **Toz said:**
> **xfce4-settings-helper** needs to be running for Alt-F2 to work in xfce/xubuntu.

   Thanks, Toz, but when I try:

```
sudo xfce4-settings-helper
```

   I do get:

```
Failed to connect to session manager: FallÃ³ la conexiÃ³n al gestor de sesion: SESSION_MANAGER environment variable not defined

(xfce4-settings-helper:4202): xfce4-settings-helper-CRITICAL **: RANDR extension is too old, version 1.1. Display settings won't be applied.
```

   I can not make work any other hotkey, I don't know why.

---

### Post by Sopalajo de Arrierez on 2011-12-26
> **VTPoet said:**
> I don't know how OCD you are about things working the way they're 'supposed' to work, but you could always install Synapse and map it to Alt+F2. Synpase allows you to run commands. Gets you the same thing, I think.

   Hey, thanks, VTPoet. This did the fix for me :-D .
   I just assigned the Synapse opening key to "Alt+F2", and now I do have a (even better) launcher.
   Thanks a lot, friend :-).

---

### Post by Toz on 2011-12-26
> **Sopalajo de Arrierez said:**
> Thanks, Toz, but when I try:

```
sudo xfce4-settings-helper
```

   I do get:

```
Failed to connect to session manager: FallÃ³ la conexiÃ³n al gestor de sesion: SESSION_MANAGER environment variable not defined

(xfce4-settings-helper:4202): xfce4-settings-helper-CRITICAL **: RANDR extension is too old, version 1.1. Display settings won't be applied.
```

   I can not make work any other hotkey, I don't know why.


Its not meant to be run with root privileges. Run it as your regular user account (no sudo):
```
xfce4-settings-helper
```

---

### Post by Sopalajo de Arrierez on 2011-12-26
> **Toz said:**
> Its not meant to be run with root privileges. Run it as your regular user account (no sudo):
```
xfce4-settings-helper
```

   Same results :-(. But let me paste it again, because I had forgotten one line in my above post:

```
Failed to connect to session manager: FallÃ³ la conexiÃ³n al gestor de sesiÃ³n: SESSION_MANAGER environment variable not defined

(xfce4-settings-helper:2297): xfce4-settings-helper-CRITICAL **: RANDR extension is too old, version 1.1. Display settings won't be applied.
Xlib:  extension "XInputExtension" missing on display ":1".
```

   Maybe it is some Ubuntu 11.10 bug.

---

### Post by Toz on 2011-12-26
> **Sopalajo de Arrierez said:**
> Same results :-(. But let me paste it again, because I had forgotten one line in my above post:

```
Failed to connect to session manager: FallÃ³ la conexiÃ³n al gestor de sesiÃ³n: SESSION_MANAGER environment variable not defined

(xfce4-settings-helper:2297): xfce4-settings-helper-CRITICAL **: RANDR extension is too old, version 1.1. Display settings won't be applied.
Xlib:  extension "XInputExtension" missing on display ":1".
```

   Maybe it is some Ubuntu 11.10 bug.

What does the following return? 
```
env
```

---

### Post by Sopalajo de Arrierez on 2011-12-27
> **Toz said:**
> What does the following return? 
```
env
```

   Here you have:

```
VNCDESKTOP=ThreepWood
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=c572b16cde78e5c1288d446200000009-1324980338.247171-1385641002
SSH_CLIENT=192.168.11.104 3797 22
KONSOLE_DBUS_SERVICE=:1.0
WINDOWID=10500158
SHELL_SESSION_ID=ed1a429d8d844000a48d3fa3ff172d69
SSH_TTY=/dev/pts/0
USER=luis
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
MAIL=/var/mail/luis
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/home/luis
LANG=es_ES.UTF-8
KONSOLE_DBUS_SESSION=/Sessions/1
SHLVL=2
COLORFGBG=15;0
HOME=/home/luis
LANGUAGE=
LOGNAME=luis
SSH_CONNECTION=192.168.11.104 3797 192.168.11.110 22
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:1
PROFILEHOME=
LESSCLOSE=/usr/bin/lesspipe %s %s
_=/usr/bin/env

```

---

### Post by Toz on 2011-12-27
How are you running xfce? 
Is this a Xubuntu install or did you install xfce over another version of *buntu? If so, which one?
Are you connecting remotely to this computer? VNC? Tunnelled? If so, what does your vnc config file look like?

You're environment variables are odd. Plus you don't have a SESSION_MANAGER variable defined. Here is my env (straight xubuntu 11.10 install):
> SSH_AGENT_PID=1784
GLADE_PIXMAP_PATH=:
TERM=xterm
SHELL=/bin/bash
XDG_MENU_PREFIX=xfce-
XDG_SESSION_COOKIE=fa7def904c6a1878d9df45fa0000000a-1324910515.899393-715653134
WINDOWID=73400324
OLDPWD=/home/toz/Development/c
GNOME_KEYRING_CONTROL=/tmp/keyring-JYZ3dd
GTK_MODULES=canberra-gtk-module:canberra-gtk-module
USER=toz
XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
GLADE_MODULE_PATH=:
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
SSH_AUTH_SOCK=/tmp/ssh-UwrFidsO1755/agent.1755
SESSION_MANAGER=local/xubi:@/tmp/.ICE-unix/1809,unix/xubi:/tmp/.ICE-unix/1809
USERNAME=toz
DEFAULTS_PATH=/usr/share/gconf/xubuntu.default.path
XDG_CONFIG_DIRS=/etc/xdg/xdg-xubuntu:/etc/xdg:/etc/xdg
PATH=/home/tpaulic/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=xubuntu
PWD=/etc
GNOME_KEYRING_PID=1746
LANG=en_CA.UTF-8
MANDATORY_PATH=/usr/share/gconf/xubuntu.mandatory.path
GDMSESSION=xubuntu
SHLVL=1
HOME=/home/toz
LANGUAGE=en_CA:en
LOGNAME=toz
XDG_DATA_DIRS=/usr/share/xubuntu:/usr/local/share/:/usr/share/:/usr/share
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-pEFwrMTBgp,guid=037e618da4c57d9cc763237e00000043
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0.0
GLADE_CATALOG_PATH=:
LIBGLADE_MODULE_PATH=:
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=Terminal
XAUTHORITY=/home/toz/.Xauthority
_=/usr/bin/env


---

### Post by Sopalajo de Arrierez on 2011-12-28
> **Toz said:**
> How are you running xfce? 
Is this a Xubuntu install or did you install xfce over another version of *buntu? If so, which one?
Are you connecting remotely to this computer? VNC? Tunnelled? If so, what does your vnc config file look like?

You're environment variables are odd. Plus you don't have a SESSION_MANAGER variable defined. Here is my env (straight xubuntu 11.10 install):

   Yes, you are right, I am connecting to XFce via VNC (VNC4Server). Sorry, I didn't told because I didn't know it could be relevant.
   Here is my ~/.vnc/xstartup (I have made several attemps and changes, so this is the last one I do use):

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
# x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
 x-window-manager &

konsole

xfce4-session
xfce4-settings-helper

```

---

### Post by Toz on 2011-12-28
If synapse solves your issue, then you should probably stick with it. 

If you want to get xfce4-settings-helper to work, I would suggest trying the following .xstartup file:
```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
# x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
 x-window-manager &

/usr/bin/startxfce4

```

Once connected, make sure that xfce4-settings-helper is running in xfce's autostart (Settings Manager -> Session and Startup -> Application Autostart)

---

### Post by Sopalajo de Arrierez on 2011-12-28
No way, friend Toz :-(. Helper keeps stopped :'-(
   But don't worry, Synapse makes the trick OK.

   Thanks a lot for your help. :)

---

### Post by seul on 2012-08-05
> **hhh said:**
> You should be able to fix this by going to Settings>>Xfce 4 Settings Manager>>Keyboard>>Application Shortcuts and add a new command called xfrun4 with the shortcut command of your choice.
Thanks hhh, fixed my problem!

---

