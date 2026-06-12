---
title: "fix error when type xfce4-session-settings"
date: 2018-03-18
forum: Desktop Environments
---

### Post by rashedayyash on 2018-03-18
[COLOR=#333333][FONT=sans-serif]dears [/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]when me type : xfce4-session-settings[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]these message shown : (xfce4-session-settings:1551): xfce4-session-settings-CRITICAL **: Unable to query session manager for client list: The name org.xfce.SessionManager was not provided by any .service files   [/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]please your help to fix the problem ,[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]BR[/FONT][/COLOR]

---

### Post by again? on 2018-03-18
What release are you using?
Is dbus-daemon running?

---

### Post by rashedayyash on 2018-03-19
[IMG]https://www.photobox.co.uk/my/photo?album_id=5284286228&photo_id=500664924848[/IMG]release 16.04   
[IMG]https://image.ibb.co/gDdKcx/sys_dbus.jpg[/IMG]

---

### Post by again? on 2018-03-19
If you give minimal information you can only expect minimal help.
Is the dbus-daemon running?
```
ps -ef | grep [d]bus-daemon
```

Did you install Xubuntu or Ubuntu and install xfce packages/xubuntu-desktop?

Output for
```
lsb_release -a
echo $DESKTOP_SESSION $XDG_CURRENT_DESKTOP 
```

---

### Post by kerry_s on 2018-03-19
sudo apt install xubuntu-desktop

are you running in vm?

---

### Post by rashedayyash on 2018-03-19
no i running in lubuntu

---

### Post by rashedayyash on 2018-03-19
[IMG]https://image.ibb.co/jF6a0H/PROB1.jpg[/IMG]

---

### Post by kerry_s on 2018-03-19
then why are you trying to run xfce4-session-settings?

yours would be: preferences-> default applications lxsession

---

### Post by rashedayyash on 2018-03-19
i want to run vinoserver at startup "when me logon by user " autostart vino

---

### Post by kerry_s on 2018-03-19
so then, in lubuntu:
menu-> preferences-> default applications lxsession-> autostart

---

### Post by rashedayyash on 2018-03-19
thanks , can i run vino before logon user "at logon screen " 
br

---

### Post by kerry_s on 2018-03-19
i think your trying to do this:
[https://wiki.ubuntu.com/Lubuntu/RemoteDesktop](https://wiki.ubuntu.com/Lubuntu/RemoteDesktop)

---

### Post by oldos2er on 2018-03-19
[rashedayyash]("https://ubuntuforums.org/member.php?u=2088731") was spam-banned, so I'm closing this thread.

Anyone with a similar problem, please create a new thread.

Closed.

---

