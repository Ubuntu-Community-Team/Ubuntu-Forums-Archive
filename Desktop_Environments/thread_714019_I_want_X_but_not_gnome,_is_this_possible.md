---
title: "I want X but not gnome, is this possible?"
date: 2008-03-03
forum: Desktop Environments
---

### Post by Swinkle on 2008-03-03
Hi,

I'm building myself a MAME cabinet and I've got xmame and a frontend all working fine but I want to boot straight into lemonlauncher (the frontend) without seeing Gnome. Is this possible?

I know how to disable GDM, from searching threads on here, but from what I gather that will also stop my X server which I need running to use lemonlauncher.

Any help please?

---

### Post by fracturedmorals on 2008-03-03
Well.....if your creating a dedicated system, maybe you could install just what you need from the ubuntu minimal install disk. ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD))

Install all of your dependencies via apt-get, including GDM and then edit /etc/gdm/gdm.conf to auto-login whatever user you specify using the session you want to use.

I'm not too familiar with the application you're trying to run, but I hope that this at least helps a bit. :)

---

### Post by kellemes on 2008-03-03
I also don't know anything about the app you're trying to run.. but maybe it's best to simply replace Gnome with some lighter window-manager? Like [Fluxbox]("http://fluxbox.sourceforge.net/"), [Openbox]("http://icculus.org/openbox/index.php/Main_Page"), [Icewm]("http://www.icewm.org/") or one of the many others that don't take over your system like Gnome.
See [http://xwinman.org/]("http://xwinman.org/") for the many choices you have..

---

### Post by spupy on 2008-03-03
If you choose Fluxbox for example. You can start fluxbox from the command line (without GDM), it takes only 5MB RAM. Then add your program to the fluxbox startup script, so it runs everytime when fluxbox loads. And finally, add a command that makes your program go fullscreen. For this you can use the tool called 'wmctrl'.
I can give you the commands if you want. It's 3 lines long. ;)

---

### Post by Swinkle on 2008-03-04
Thanks guys but that's not really what I meant. My fault for not explaining it very well.

My problem isn't anything to do with Gnome in particular, what I meant is that I don't want to see any desktop environment at all, I just want to load a fullscreen X application from the command line without having to see a desktop environment.

Is it possible to load X applications (nothing specifically to do with the application I'm using, just any X app in general) without being inside a desktop environment? 

I've tried doing startx from a command line after killing gdm but it just seems to restart gdm along with X :(

---

### Post by eriqjaffe on 2008-03-04
You might be able to do that using an .xinitrc file that** just** runs Lemonlauncher?  Invoke it with...

```
startx -x .xinitrc
```

Don't know if that'll actually work or not, but...

---

### Post by ShodanjoDM on 2008-03-04
Not sure if this what you want, but maybe you can try:

```
sudo aptitude install xdm
```

xdm - X display manager

---

### Post by spupy on 2008-03-04
OK, this is how you do it:
1. In your home dir, create a file named ".xinitrc"
2. In this file enter
```
exec programname
```
3. Type startx

Just now I'm running firefox that way! :cool: But I'm not sure if the app starts fullscreen.

---

