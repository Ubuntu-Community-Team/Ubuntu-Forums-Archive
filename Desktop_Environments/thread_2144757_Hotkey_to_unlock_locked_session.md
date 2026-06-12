---
title: "Hotkey to unlock locked session"
date: 2013-05-13
forum: Desktop Environments
---

### Post by kubco2 on 2013-05-13
Hello,

I want use some long shortcut to unlock session,  it is because I have very strong and long password, and set "lock session" after short period of inactivity, because of security...... It can be nice if I can unlock with hotkey at HOME ...

It must be possible to implement such thing, just need some hints ...

I have ubuntu 12.10 gnome remix, and use Gnome, xscreensaver.

Thanks for help.

---

### Post by kubco2 on 2013-05-14
bump

---

### Post by Frogs Hair on 2013-05-14
Unlocking the screen will require a password for the security reasons you cited. Editing the sudoers configuration is possible, but not recommended unless you know exactly what you are doing. You may end up locked out of the operating system or eliminating password security all together  . I don't know if it is possible  limit changes to the sudoers configuration to one action such as screen lock and tie a key binding to the change.

---

### Post by stinkeye on 2013-05-14
I don't think keyboard shortcuts work from the lockscreen.

I save my password in GNOME keyring and use [**_[COLOR="#B22222"]easystroke[/COLOR]_**]("http://sourceforge.net/apps/trac/easystroke/wiki/Documentation") to type my password 
with a spare mouse button.
Works when authenticating for sudo and at the lockscreen.
Only need to manually type my password at the initial login screen.
See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2125918").

---

### Post by kubco2 on 2013-05-15
stinkeye:
thank you for this equivalent....
I had to replace sensitive characters to xdotool keyname with sed, and now it works fine ...

---

