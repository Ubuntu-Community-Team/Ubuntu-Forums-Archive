---
title: "Hardy Headless unit cannot startx"
date: 2008-05-28
forum: Desktop Environments
---

### Post by jombeewoof on 2008-05-28
When i try to run startx from an ssh session I get an error to the effect that I don't have permissions. (at work now, and machine isn't on so I can't test)

I have installed icewm and the X server core, and I'm pretty sure it will work if I hook up a monitor and keyboard, but I want it to work through a VNC session or something like that. 

internal network only, don't really need access from outside.

I've read a thousand threads about this, but they're mostly for older versions of Ubuntu or X.


I know it's something silly, a little argument I need to add, or a flag I need to set in xorg.conf or something.

---

### Post by damis648 on 2008-05-28
For what purpose would this make? As far as i know, SSH will always only display a terminal. If you want VNC, i think Ubuntu has this built in by default anyway. If you do not have default Ubuntu, Google VNC and you will find several good ones that can be accessed via browser or a VNC viewer.

---

### Post by jombeewoof on 2008-05-28
> **damis648 said:**
> For what purpose would this make? 

I would like to be able to get to a full on desktop for my headless unit if the need should ever arise.

> As far as i know, SSH will always only display a terminal. 

There are ways of getting around this. Putty for instance does X11 forwarding.


> If you want VNC, i think Ubuntu has this built in by default anyway. If you do not have default Ubuntu, Google VNC and you will find several good ones that can be accessed via browser or a VNC viewer.

Default Ubuntu Hardy bare Server setup.
I have installed samba, ushare, vsftp. that's pretty much it.

None of "google's" help docs work because I don't have a traditional monitor and keyboard setup. I just have remote access.

---

### Post by sderrick on 2008-05-28
This may help

[http://www.quietearth.us/articles/2006/08/24/Ubuntu-Enabling-remote-Xwindows](http://www.quietearth.us/articles/2006/08/24/Ubuntu-Enabling-remote-Xwindows)

Scott

---

### Post by jombeewoof on 2008-05-28
> **sderrick said:**
> This may help

[http://www.quietearth.us/articles/2006/08/24/Ubuntu-Enabling-remote-Xwindows](http://www.quietearth.us/articles/2006/08/24/Ubuntu-Enabling-remote-Xwindows)

Scott


or if you prefer to edit /etc/gdm.conf by hand, make sure there are no overriding settings in /etc/gdm.conf-custom. Under the security section change DisallowTCP to false.

That's what I was looking for, must be pretty much the same for KDM, if not, I'll just install gdm.

Thanks.

---

### Post by jombeewoof on 2008-05-28
I don't get the permissions error, but I'm getting keyboard errors.

total output here
[http://pastebin.com/f61ee5a4f](http://pastebin.com/f61ee5a4f)

Xorg log here
[http://pastebin.com/d4abedd6b](http://pastebin.com/d4abedd6b)

---

### Post by jombeewoof on 2008-05-31
bump

---

