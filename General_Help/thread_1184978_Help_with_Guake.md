---
title: "Help with Guake"
date: 2009-06-11
forum: General Help
---

### Post by dr.pepper23 on 2009-06-11
I just learned about Guake after using Yakuake for a few months. I figured I'd use Guake as it uses GNOME and it works fine, except whenever it drops down over an open menu the background is replaced with my Desktop background instead of showing the open folder behind it. Screenshot is attached. Is there any way to fix this? Thanks.

---

### Post by lightstream on 2009-06-11
I think it's probably normal - I don't use Guake, but that effect sounds the same as what happens if you set panels in Gnome to 'transparent' - not really transparent at all, just shows the corresponding portion of your wallpaper.

There are screenshots on the Guake site, I'm not sure but this one appears to resemble yours: [http://trac.guake-terminal.org/screenshots/5](http://trac.guake-terminal.org/screenshots/5)

---

### Post by dr.pepper23 on 2009-06-11
Yea I thought about that until I saw the shot here:  [http://trac.guake-terminal.org/screenshots/1](http://trac.guake-terminal.org/screenshots/1)
It looks like he solved the problem somehow...

---

### Post by lovinglinux on 2009-06-11
I'm using [tilda](apt:tilda) [apt-get] instead of guake and I like it very much, specially because I can set the position of the terminal window on the screen, not just the size of it. Additionally, it doesn't have issues with transparency.

I gave up on Guake when installed Jaunty, because it uses Python 2.5 instead of Python 2.6 (installed by default on Jaunty). Python 2.5 is not playing well with Jaunty and increases CPU usage a lot. If you have CPU issues, I would recommend checking which applications are still dependent on Python 2.5 and if there isn't any essential package associated with it, then you could remove it. Make sure you have Python 2.6 before doing this.

The only applications dependent on Python 2.5 on my machine were guake, mimms and ontv. Since I can live without them, I prefer the performance improvement provided by their removal.

---

### Post by dr.pepper23 on 2009-06-12
I was actually looking at tilda and guake and figured I'd go with guake cause it said it was build for GNOME. But I'll definitely give tilda a try now, especially because of the python issue. Thanks a lot guys.

---

### Post by DouglasCaixeta on 2009-06-25
> **lovinglinux said:**
> I'm using [tilda](apt:tilda) [apt-get] instead of guake and I like it very much, specially because I can set the position of the terminal window on the screen, not just the size of it. Additionally, it doesn't have issues with transparency.


I try tilda and I'm having the same problem here. Transparency is behaving like in Guake.
I think is a system problem. There is a way to fix it?

---

### Post by dr.pepper23 on 2009-06-25
You should be able to go to preferences > appearance> and check enable transparency. It worked just fine for me.

---

### Post by DouglasCaixeta on 2009-06-26
> **dr.pepper23 said:**
> You should be able to go to preferences > appearance> and check enable transparency. It worked just fine for me.

Where is this?
In Appearance, in which tab?
I didn't find this option, even in Visual effects tab, and them Custom.

---

### Post by dr.pepper23 on 2009-06-27
Sorry, I left out an important step. Ok, first press f12 (or whatever key you have assigned as) to bring up the the terminal window. Then right click on the terminal window and you should see "Preferences," second from the bottom. Then click "Appearance" tab and check "Enable Transparency." You can also use the slider to adjust the level of transparency. Hope this helps!

---

### Post by DouglasCaixeta on 2009-06-27
> **dr.pepper23 said:**
> Sorry, I left out an important step. Ok, first press f12 (or whatever key you have assigned as) to bring up the the terminal window. Then right click on the terminal window and you should see "Preferences," second from the bottom. Then click "Appearance" tab and check "Enable Transparency." You can also use the slider to adjust the level of transparency. Hope this helps!

I did that, since the beginning. But the transparency that appears is only my wallpaper. If I have another window in between, like this screen of Firefox, and open Guake, it will appear the wallpaper, not this window. So, its not a true transparency. And that happens with Guake or Tilda, or other terminal. I already tried 3 or 4.

That's why I think the problem is with the system, not with the terminal.

---

### Post by DouglasCaixeta on 2009-06-27
dr.pepper23, do you have the Visual Effects of Ubuntu enabled?

System > Preferences > Appearance. Then tab Visual Effects.

---

### Post by dr.pepper23 on 2009-06-27
> **DouglasCaixeta said:**
> dr.pepper23, do you have the Visual Effects of Ubuntu enabled?

System > Preferences > Appearance. Then tab Visual Effects.

Yep. If I turn the visual effects off then tilda just goes black, doesn't even show wallpaper. Hmm...I don't really know what the problem is. Maybe has something to do with Compiz? I don't know, just throwing that out there.

By the way, I never got Guake to work, but I am using Tilda and it is working like it should.

---

### Post by DouglasCaixeta on 2009-06-27
Yes, that is my problem. Withot visual effects enabled, no transparency.
Tilda has a problem with focus, so I prefer Guake.

Anyway, thanks.

---

### Post by end3rkid on 2009-11-04
There's not a fix for this issue yet?

---

### Post by dr.pepper23 on 2009-11-04
Not that I know of. I just started using Tilda. It does the exact same thing, just better. Give it a shot.

---

### Post by end3rkid on 2009-11-12
For a unknown reason, the transparency is working perfectly today (after update to the latest Linux Kernel)

[IMG]http://i34.tinypic.com/2rr9jwo.png[/IMG]

---

### Post by ClyN3il on 2011-10-20
Has anyone figured this out yet? I'm still having the same problem now in Oneiric. I've definitely had the transparency working before. BTW, right now, transparency doesn't work in Guake, but it does in Gnome Terminal. I suspect it has something to do with fglrx. I think it was working before I installed fglrx.

---

### Post by lovinglinux on 2011-10-21
> **ClyN3il said:**
> Has anyone figured this out yet? I'm still having the same problem now in Oneiric. I've definitely had the transparency working before. BTW, right now, transparency doesn't work in Guake, but it does in Gnome Terminal. I suspect it has something to do with fglrx. I think it was working before I installed fglrx.

Please create a new thread. This one is very old and a lot of things have changed since it was created.

Closing.

---

