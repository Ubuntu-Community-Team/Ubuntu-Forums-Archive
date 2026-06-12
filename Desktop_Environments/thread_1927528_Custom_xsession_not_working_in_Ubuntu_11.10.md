---
title: "Custom xsession not working in Ubuntu 11.10"
date: 2012-02-18
forum: Desktop Environments
---

### Post by mrmiagi99 on 2012-02-18
Hi 

I'm not sure if this problem has already been posted here, so here goes: 

I'm trying to setup my own custom session in Ubuntu 11.10 but every time I try to login with this session the screen goes black and I am sent back to the login screen. I'm new to this so I'm not really sure where to go look for error concerning this particular problem. It was working perfectly with the previous version, 11.04. 

My .desktop file: 
```
[Desktop Entry]
Encoding=UTF-8
Name=Compiz
Comment=Compiz-Fusion standalone
Exec=/usr/local/bin/compiz-session
Type=Application
```

My session execute file: 
```
#!/bin/bash
if test -z "$DBUS_SESSION_BUS_ADDRESS"; then
    eval `dbus-launch --sh-syntax --exit-with-session`
fi
compiz --replace ccp & wmpid=$!
sleep 1
if [ -f ~/.compiz-session ]; then
    source ~/.compiz-session &
else
    xterm &
fi
# Wait for WM
wait $wmpid
```

My session file in home directory: 
```
#! /bin/bash
ck-launch-session dbus-launch compiz &
ck-launch-session dbus-launch gnome-settings-daemon &
ck-launch-session dbus-launch synapse
```

Thanks

---

