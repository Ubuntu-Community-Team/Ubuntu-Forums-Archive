---
title: "VNC not reading xstartup"
date: 2007-02-17
forum: Desktop Environments
---

### Post by dignus on 2007-02-17
Guys,

I've just setup vncserver, it works. But .. I'd like to run my favourite wm, fluxbox.

I've setup ~/.vnc/xstartup as follows:

xrdb $HOME/.Xresources
xsetroot -solid grey
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
startfluxbox &

but.... when I start vncserver and login, I'm getting xfce4 (it's been installed on this box). Any idea why vncserver is ignoring my xstartup?

---

### Post by Pom2122 on 2007-02-17
Hi dignus,

It's been a while since I ran vnc (switched to x11vnc) but I think there is a file in /home/*username]*.vnc named xstartup. Open it with a text editor and there should be a line that says ```
twm
``` Replace it with ```
startfluxbox
```

Make a backup copy of the file just in case.:)

---

### Post by dignus on 2007-02-18
> **Pom2122 said:**
> Hi dignus,

It's been a while since I ran vnc (switched to x11vnc) but I think there is a file in /home/*username]*.vnc named xstartup. Open it with a text editor and there should be a line that says ```
twm
``` Replace it with ```
startfluxbox
```

Make a backup copy of the file just in case.:)

Uhm yeah.. thanks. But as you could've read, I already did that :) vncserver seems to ignore my xstartup file.

---

### Post by Pom2122 on 2007-02-18
Apologies. This is why I should never post shortly after waking up! :oops:

---

