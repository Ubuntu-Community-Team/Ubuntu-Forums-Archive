---
title: "BlackBox VNC with xstartup"
date: 2006-02-01
forum: Desktop Environments
---

### Post by SadaraX on 2006-02-01
I am trying to start a blackbox vnc session on my computer here, but it keeps starting KDE instead. I found that I did not have an ~/.vnc/xstartup file, so I wrote one. It is as follows:

```

[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
#xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
blackbox &

```

I have blackbox installed via apt-get, but vnc still starts up KDE. I even logged out of my desktop system and tried to log back in through KDM using a BlackBox session type. But it still started KDE. When I logged out, it said that it had used BlackBox previously, even though it had not. 

I am totally baffled why vnc is completely avoiding my xstartup file and why I cannot log into anything else besides KDE, but I would really like some help.

---

