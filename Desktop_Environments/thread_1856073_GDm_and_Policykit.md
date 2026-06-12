---
title: "GDm and Policykit"
date: 2011-10-07
forum: Desktop Environments
---

### Post by crking on 2011-10-07
i have the problem withe dbus after login; it seems that dbus getting lost somewhere in the process. in instance when I want to config a connection in the network-manager i get insufficient privilege. adding ck-console and dbus in the Exec= of gdm ???.desktop does nothing in case of echinus.desktop i get back to login screen after entering pass and login and in the case of xmonad it doesn't work at all and i get insufficient privilage. i need someone to tell me how could I remove this obstacle?

te policykit suppose to kick in istead of showing insufficient privilage.
ps: I have not this problem on openbox
ps2: gdm suppost to invoke the consolekit and dbus automatically. but except the openbox it doesn't ( xmonad echins fvwm ....)

```

]>ck-list-sessions
Session125:
    unix-user = '1000'
    realname = 'amin'
    seat = 'Seat1'
    session-type = ''
    active = TRUE
    x11-display = ':0'
    x11-display-device = '/dev/tty8'
    display-device = ''
    remote-host-name = ''
    is-local = TRUE
    on-since = '2011-10-07T13:24:43.107820Z'
    login-session-id = '4294967295

```

---

### Post by crking on 2011-10-07
look a discovery " i typed /usr/lib/polkit-gnome/polkit-gnome-authentication-agent-1 in terminal then enter and my command line went standby then i went to network manager and start editing a vpn connection and then i get the policykit password dialog and i enterd it and all set" but the this is why it doesn't kick in automatically? should "/usr/lib/polkit-gnome/polkit-gnome-authentication-agent-1"
 starts automativally?

```
/usr/lib/polkit-gnome/polkit-gnome-authentication-agent-1

(polkit-gnome-authentication-agent-1:7082): polkit-gnome-1-WARNING **: No icon for themed icon with name 'nm-icon'
```

---

