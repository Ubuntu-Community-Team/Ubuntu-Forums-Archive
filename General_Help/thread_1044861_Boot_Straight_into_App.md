---
title: "Boot Straight into App"
date: 2009-01-19
forum: General Help
---

### Post by Brian96 on 2009-01-19
I did a little searching, but couldn't find exactly what I was looking for.

I have an old PC laying around that I've been using for my preschoolers to play Gcompris. I've been running it with a server install and basic XFCE4 desktop environment (because at the time I was quite new and knew how to use XFCE to create a clean desktop with nothing but the app launcher).

I'm wondering how I would go about setting it up to boot straight into Gcompris. I would be starting with a clean install.

I'd like to have as little more than X and Gcompris on it as possible. Even a barebones XFCE4 was a little bulky for this machine.

Thanks in advance.

---

### Post by adamlau on 2009-01-19
Verify that 'Settings > Settings Manager > Sessions and Startup> General > Automatically save sessions on logout' is checked. Leave Gcompris open when you shutdown your box.

---

### Post by tacutu on 2009-01-19
I think your .xinitrc (in your home folder) should contain 
```
exec gcompris
```
this way, when X starts, gcompris will start automatically (without any kind of window manager, etc.)

---

### Post by Brian96 on 2009-01-23
> **tacutu said:**
> I think your .xinitrc (in your home folder) should contain 
```
exec gcompris
```
this way, when X starts, gcompris will start automatically (without any kind of window manager, etc.)

Thanks, I'll give that a try!

---

### Post by Brian96 on 2009-01-24
> **tacutu said:**
> I think your .xinitrc (in your home folder) should contain 
```
exec gcompris
```
this way, when X starts, gcompris will start automatically (without any kind of window manager, etc.)

That worked, thanks.

Now I've got a really old machine (Celeron 400 Mhz) set up to boot straight into gcompris. Pretty cool!

---

