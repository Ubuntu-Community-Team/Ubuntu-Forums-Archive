---
title: "Disable gdm, CLI instead and startx with fluxbox"
date: 2005-12-08
forum: Desktop Environments
---

### Post by dartakaum on 2005-12-08
Hy!

Now i'm using gdm starting fluxbox with it.

How can i change to disable gdm startup, and when i do startx start fluxbox instead?


thanks.

---

### Post by fourchannel on 2005-12-08
i'm sure there is a better way to do this.

but you could disable execute permissions on your /etc/init.d/gdm file

```
sudo chmod 644 /etc/init.d/gdm
``` 
and then for fluxbox you would need to go to your home directory and make a file called .xinitrc

and in that file you need to have
```
exec fluxbox
``` 
if you wanted programs to automatically load when you start flux, then in the .xinitrc file you would place them before 'exec fluxbox'

so for example, to launch firefox when i login.

```
firefox
exec fluxbox
```

---

### Post by dartakaum on 2005-12-15
well, i done chmod -x gdm, and added fluxbox to .initrc.
:)
it works well.

---

### Post by schilcha on 2005-12-15
Try
```
sudo update-rc.d -f gdm remove
```
to avoid that gdm is started at boot-time.

---

