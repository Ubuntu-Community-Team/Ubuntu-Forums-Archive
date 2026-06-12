---
title: "remove Ubuntu Logo from Loginscreen - 18.04 - displaymanager gdm3"
date: 2018-12-11
forum: Desktop Environments
---

### Post by youbunny on 2018-12-11
*ubuntu 18.04 / gnome*


Hi,

I'm fairly new and I tried to customize my displaymanger on ubuntu in order to remove the ubuntu logo you see when you log in after starting up.
I found ways to customize the [background]("https://vitux.com/how-to-change-login-lock-screen-background-in-ubuntu/"), [how change the display manager]("https://vitux.com/some-common-ubuntu-display-managers-and-how-to-switch-between-them/") but no way how to remove the ubuntu logo on the bottom.

I found some options available with
```
sudo gedit /usr/share/gdm/gdm.schemas
```
```
sudo gedit /etc/gdm3/greeter.dconf-defaults
```
```
sudo gedit /etc/gdm3/custom.conf
```


but none of these helped me to remove the ubuntu logo.

What could I try or does anyone know?

Thank you so much :)

---

### Post by mc4man on 2018-12-11
The only thing I have that uses gdm3 is a small 19.04 install. On it to get rid of the logo - 
```
sudo mv /usr/share/plymouth/ubuntu-logo.png /usr/share/plymouth/ubuntu-logo.png.bak
```
And reboot
(- if desired you could then replace with icon of choice (a png within reason), just name it ubuntu-logo.png

edit: you should refrain from going sudo gedit ...

---

### Post by youbunny on 2018-12-12
Thank you so much, this worked!

Is this common practice to rename files that shouldn't be used anymore with .bak (short for backup) at the end?
What if I would want to use two backups, how would I change another one, .bak2?


Why s[COLOR=#000000]hould I refrain from going sudo gedit?

I hope I don't ask in a bad way. Thank you so much :)[/COLOR]

---

### Post by The Cog on 2018-12-12
> **youbunny said:**
> Is this common practice to rename files that shouldn't be used anymore with .bak (short for backup) at the end?
Fairly common.
> What if I would want to use two backups, how would I change another one, .bak2?
That's as good as any unless you want longer and more descriptive names.
> Why should I refrain from going sudo gedit?

Graphical apps often drop configuration files in the user's home directory. If you run an app under sudo, it can drop root-owned files in your home making it difficult for you to use the apps in future when the app can't properly read and write its configuration files as you any more.

I tyy to avoid this by using **sudo -i** which sets $HOME to /root and other such things, and then running the app, e.g.
```
sudo -i
gedit wotsit.txt
```
Probably others will say this is still wrong, but it seems to work for me.

---

### Post by youbunny on 2018-12-12
Thank you so much! 
Makes all sense

I just don't understand the sudo part fully I think. 

I looked it up and think you meant the -H parameter?
While -i gives sudo until you exit it with exit?

I see how a graphical application started with sudo might create additional files that have permissions that might cause problems when read with non privileges again?

But how to get around it best, that's something I have trouble wrapping my mind around atm..

---

### Post by CatKiller on 2018-12-12
> **youbunny said:**
> I just don't understand the sudo part fully I think. 
Sudo runs a command as a different user, but it doesn't change any environment variables. You are still your user, with your home folder and whatnot, just with different permissions.

Sudo -i simulates logging in as root, so you have root's permissions, but also root's home folder, command line customisations, and everything, till you log out again from that session.

---

### Post by mc4man on 2018-12-12
> **youbunny said:**
> Thank you so much! 
Makes all sense

I just don't understand the sudo part fully I think. 

I looked it up and think you meant the -H parameter?
While -i gives sudo until you exit it with exit?

I see how a graphical application started with sudo might create additional files that have permissions that might cause problems when read with non privileges again?

But how to get around it best, that's something I have trouble wrapping my mind around atm..
You can use sudo -i  which then puts you on a root prompt (#), then run command (sudo not needed
ex.
```
sudo-i
```
```
gedit /usr/share/gdm/gdm.schemas
```
or
go sudo -H command
ex.
```
sudo -H  gedit /usr/share/gdm/gdm.schemas

```

---

