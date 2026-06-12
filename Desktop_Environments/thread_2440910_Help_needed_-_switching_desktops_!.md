---
title: "Help needed - switching desktops !"
date: 2020-04-16
forum: Desktop Environments
---

### Post by yuri-weinstein on 2020-04-16
Hello all
Have a problem and need your help
I installed 20.04 beta and then tried adding and switching desktops from gnome to unity 
I believe all did was installed unity and ran: 

```

sudo dpkg-reconfigure gdm3
```
and rebooted 

Then I wanted to switch back and I see desktop looking as unity altho I logged in to gnome (I belive)

And now see some odd behavior with settings etc.
When I check 

```

DESKTOP_SESSION=unity
```

But 

```

ls /usr/bin/*session
/usr/bin/dbus-run-session  /usr/bin/gnome-session  /usr/bin/gnome-session-custom-session
```

That looks incorrect to me, but I am hesitant to make any changes and hope someone expert here can help with exact steps how to fix it

---

### Post by CelticWarrior on 2020-04-16
Installing Unity doesn't require reconfiguration of gdm3. Just install it and then select it before logging in.

---

### Post by QIII on 2020-04-16
Please use the default font and color.  Please include all terminal commands and results in code tags.

---

### Post by grahammechanical on 2020-04-19
I am on 20.04 and I am definitely using Unity. The rubbish bin is at the bottom of the dock. But I get exactly the same readout from that command.

> graham@sdb7-Zesty:~$ ls /usr/bin/*session
/usr/bin/dbus-run-session  /usr/bin/gnome-session-custom-session
/usr/bin/gnome-session

I am finding that the dash is empty of applications but the chosen apps are all in the dock. I think we are getting to the end of the road with Unity.

Regards.

---

