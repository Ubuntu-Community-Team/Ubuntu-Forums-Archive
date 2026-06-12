---
title: "Remote desktop says authentication failed"
date: 2011-01-25
forum: Desktop Environments
---

### Post by b89.smith on 2011-01-25
I am running an updated copy of 10.04 LTS desktop. I have firewalled all the ports on my desktop except port 22. To remote desktop I SSH into my computer and setup a tunnel from 5900 to localhost:5900. This normally works and lets me securely access my desktop. Recently when I open VNC it asks me for a password, which I type in. Then it says authentication failed. I tried removing the password in my Remote Desktop Preferences on my Ubuntu desktop, but this did not fix the problem and my VNC client continued to ask for a password. Is there a way I can reset my VNC settings? I feel like some how my configuration became corrupt and that is the reason I continue to not be able to login to my system through VNC.

Thanks

---

### Post by Krytarik on 2011-01-25
I believe the file in which the password is stored is located in ~/.vnc or similar, look for it, then simply delete it.

---

### Post by b89.smith on 2011-01-26
I don't have a .vnc directory in my home folder. I believe .vnc is only created when you use vncserver, not Preferences > Remote Desktop

---

### Post by asmoore82 on 2011-01-26
The VNC "Remote Desktop" server embedded into the modern Gnome desktop (`vino-server`)
stores the VNC password encrypted in the keyring.

Sometimes I used to find it helpful to ```
killall vino-server
``` but
I just now tried this on my 10.04 LTS box and it doesn't seem to respawn anymore.
Whoops!

At any rate a reboot or logout/login should have the same effect.

Did you know if you install a package that provides the command line `vncviewer`
such as "xtightvncviewer" you can have it build the ssh tunnel for you like this:
```
vncviewer -bgr233 -via <user>@<remote_host> localhost
```
^since you've already done some tunneling by hand you already know
that the last bit there really should always be "localhost"
For anyone else who's confused by this, think of it as specifying the VNC host
from the point of view of inside the SSH tunnel created by `-via`

`-bgr233` color reduction really helps out a lot on a slow connection.

---

### Post by Krytarik on 2011-01-26
> **b89.smith said:**
> I don't have a .vnc directory in my home folder. I believe .vnc is only created when you use vncserver, not Preferences > Remote Desktop
Sorry, I didn't get that in the first place.

Wouldn't it be sufficient just to run vino-server after killall, like this?:
```
killall vino-server && vino-server
```Anyways, I'm curious if it helps in this case.

---

### Post by asmoore82 on 2011-01-26
> **Krytarik said:**
> Wouldn't it be sufficient just to run vino-server after killall, like this?

No, `vino-server` must be embedded within the Desktop session that it's sharing.

This used to work but doesn't seem to anymore either:
```
DESKTOP=:0 vino-server
```

---

### Post by b89.smith on 2011-01-27
Restarting or rebooting the computer does not fix the problem. 

My tunnels are all correct. When I attempt to VNC into the linux box a password dialog box appears. So I know it is connecting just not authenticating.

---

