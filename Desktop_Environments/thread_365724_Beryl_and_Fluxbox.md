---
title: "Beryl and Fluxbox"
date: 2007-02-20
forum: Desktop Environments
---

### Post by lucia_engel on 2007-02-20
I'm currently using fluxbox and I'd like to get beryl going. I understand that they are both windows manager thus cannot coexist. 

Shouldn't it be possible that I just use beryl on its own then without any previous WM or desktop environment?
Or must beryl be installed with a desktop environment? If yes, then installing *xfce4* would work right? I don't want the whole xubuntu package.

I plan to make this .xinitrc script:
```
#!/bin/sh
 beryl-manager
 sleep 4
 exec xfce4-session
```

---

### Post by tonyr1988 on 2007-02-20
Slight correction: Beryl is not a desktop environment - it's a compositing window manager. There's a difference between a DE and a WM. Unlike other operating systems, Linux keeps the window management (X, Beryl, etc.) separate from the graphical interface (GNOME, KDE, Fluxbox - the wallpaper, panels, icons, drag / drop, etc.)

Unfortunately, I can't help much with your problem - I see no reason why you cannot use Beryl on top of Fluxbox. IIRC, Beryl doesn't have as many (if any) GNOME dependencies as Compiz did, and it can definitely be ran under KDE. But I'm not a Beryl expert by any stretch of the word (I just use it :P) - I'm not even 100% sure what I said above was correct (can someone verify it?)

You may want to check the beryl forums for beryl-specific questions. Not that the users here can't help you, but there will be a more specific scope on the beryl forums (and the actual developers :D)

---

### Post by yabbadabbadont on 2007-02-20
You can't have both beryl and fluxbox at the same time.  They are both window managers and you can only have one window manager running at a time.  :)

See this same discussion here: [http://forums.gentoo.org/viewtopic-t-540973-highlight-.html](http://forums.gentoo.org/viewtopic-t-540973-highlight-.html)

---

### Post by lucia_engel on 2007-02-20
Thanks for the replies.

Just to elaborate...
> I understand that they are both windows manager thus cannot coexist. 



> **yabbadabbadont said:**
> They are both window managers and you can only have one window manager running at a time.

Then shouldn't it be possible to just have startx start up beryl? I should clarify that I'm willing to remove fluxbox if that's possible. How would I set that up?

If it's not possible, I guess I'll just have to install xfce4.

---

### Post by yabbadabbadont on 2007-02-20
> **lucia_engel said:**
> Then shouldn't it be possible to just have startx start up beryl? I should clarify that I'm willing to remove fluxbox if that's possible. How would I set that up?

If it's not possible, I guess I'll just have to install xfce4.

Doh!  :oops:  I missed that.  I was mostly replying to the misinformation that was being posted.

I know that I've read a howto or guide on doing exactly what you want.  I just can't remember where.  It may have been on the gentoo forums or in the gentoo wiki.  I don't see why you couldn't do what you showed in your example though.  Try it and see what happens.  The worst that can happen is that it doesn't work.  :D

If I find the guide, I'll post back here with a link.

Edit: This looks sortof like what you wanted: [http://forums.gentoo.org/viewtopic.php?t=536766](http://forums.gentoo.org/viewtopic.php?t=536766)

Edit2: You might also want to read: [http://forums.gentoo.org/viewtopic.php?t=521487](http://forums.gentoo.org/viewtopic.php?t=521487)

---

### Post by K.Mandla on 2007-02-20
> **lucia_engel said:**
> Then shouldn't it be possible to just have startx start up beryl? I should clarify that I'm willing to remove fluxbox if that's possible. How would I set that up?

If it's not possible, I guess I'll just have to install xfce4.
Yeah, you can do that. Install Beryl like you want, then edit your ~/.xinitrc file to include this. ...

```
emerald &
exec beryl
```
Take out any references to Fluxbox. It'll work, you just don't get much as a result.

[[img]http://xs312.xs.to/xs312/07082/yes-you-can.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs312&d=07082&f=yes-you-can.jpg)

No menus, no way of controlling windows, starting programs, etc. Now you can, like I did here, trigger a terminal window in your .xinitrc file and start everything manually, but that kind of stinks.

So in a way of answering your question, you can run just Beryl alone, without any frills, but you can't run it *with* Fluxbox.

---

### Post by lucia_engel on 2007-02-20
Thanks for the explanation K.Mandla. 

Having a terminal to start up programs sorta defeat the purpose of having all these eye candy doesn't it?

I'll try it with xfce then, thanks for all the help everyone.

---

### Post by K.Mandla on 2007-02-20
> **lucia_engel said:**
> Having a terminal to start up programs sorta defeat the purpose of having all these eye candy doesn't it?
Not necessarily, it just makes some things a little trickier. ;)

My point was just to show that you can run a Beryl-only setup, and avoid the entire Gnome/KDE infrastructure that generally comes with it. So while you can't run Fluxbox together with Beryl, you can run Beryl alone, and achieve the same effects.

And there are panel programs you can add that will fill in the missing parts for you. If you want to do a minimalist Beryl setup, look into fbpanel, lxpanel or perlpanel, and if you don't mind hand-editing your program menus, they'll do just fine.

(By the way, I'm going to shift this thread to Desktop Environments, which is a better location for it. Even though it's really about window managers, and not desktop environments. :roll: )

---

### Post by bonzodog on 2007-02-20
There is, in the beryl forums a post explaining how to run beryl entirely on it's own.
You need to run a prog that does a root menu, and a prog like nitrogen to change the backgrounds.
Also, you could add something like pypanel or fbpanel, and add program launchers to that.

---

### Post by lucia_engel on 2007-02-20
Thanks for the suggestions. I'll try out the various panels when I get home.

It seems that beryl doesn't handle wallpaper. If I ditch fluxbox, what standalone program can I use to manage wallpaper?

---

### Post by adamJ5 on 2007-02-20
I use xcompmgr+fluxbox instead. Works like a charm. Install xcompmgr and add 

```
xcompmgr -f -c -F
```

to your ~/.fluxbox/startup file.

---

### Post by bonzodog on 2007-02-20
> **lucia_engel said:**
> If I ditch fluxbox, what standalone program can I use to manage wallpaper?

Like I said, there is now a new program called Nitrogen, which is what I use in Openbox to change backgrounds.

[http://www.minuslab.net/code/nitrogen/](http://www.minuslab.net/code/nitrogen/)

Also, Use fbpanel for Icons, and hunt on the web for a root menu prog.

Ah, also, i'm not sure if beryl invokes gtk, in which case you will need to make sure you have gtk theming working - I use "gtk-chtheme".

---

### Post by Mateo on 2007-02-20
> **tonyr1988 said:**
> Slight correction: Beryl is not a desktop environment - it's a compositing window manager. There's a difference between a DE and a WM. Unlike other operating systems, Linux keeps the window management (X, Beryl, etc.) separate from the graphical interface (GNOME, KDE, Fluxbox - the wallpaper, panels, icons, drag / drop, etc.)

Unfortunately, I can't help much with your problem - I see no reason why you cannot use Beryl on top of Fluxbox. IIRC, Beryl doesn't have as many (if any) GNOME dependencies as Compiz did, and it can definitely be ran under KDE. But I'm not a Beryl expert by any stretch of the word (I just use it :P) - I'm not even 100% sure what I said above was correct (can someone verify it?)

You may want to check the beryl forums for beryl-specific questions. Not that the users here can't help you, but there will be a more specific scope on the beryl forums (and the actual developers :D)

I thought Metacity was gnome's WM...

---

### Post by Izkata on 2007-03-09
According to beryl-manager, Metacity is Gnome's default window manager, and KWin is KDE's default.  (And I'm saying, according to that, since I'm still new to Linux :D )

---

### Post by macogw on 2007-03-22
> **K.Mandla said:**
> Yeah, you can do that. Install Beryl like you want, then edit your ~/.xinitrc file to include this. ...

```
emerald &
exec beryl
```
Take out any references to Fluxbox. It'll work, you just don't get much as a result.

[[img]http://xs312.xs.to/xs312/07082/yes-you-can.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs312&d=07082&f=yes-you-can.jpg)

No menus, no way of controlling windows, starting programs, etc. Now you can, like I did here, trigger a terminal window in your .xinitrc file and start everything manually, but that kind of stinks.

So in a way of answering your question, you can run just Beryl alone, without any frills, but you can't run it *with* Fluxbox.

Map keyboard shortcuts in Beryl for common tasks.  There are a dozen available.  Make sure one of them is a terminal.

---

