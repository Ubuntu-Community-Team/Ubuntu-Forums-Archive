---
title: "ugly fonts"
date: 2007-03-15
forum: Desktop Environments
---

### Post by jmvidalvia on 2007-03-15
I've got xubutu edgy.
My fonts look ugly, so i tried to read [http://www.ubuntuforums.org/showthread.php?t=235526](http://www.ubuntuforums.org/showthread.php?t=235526) to improve them, but 32 pages are too much for me.
Isn't there any standard solution in any how-to yet?
I already installed ttmscorefonts and actived anti-alising and chose the suitable fonts from Firefox and add 96 dpi in conf.list.
All "easy" solutions have been improved, without success...

---

### Post by chewearn on 2007-03-15
I have no issue with how my fonts look.  Maybe you should post a screen shot; others in this forum might be able to tell whether your fonts are ok or not.

---

### Post by jmvidalvia on 2007-03-15
I have 3 systems in my laptop.
XP looks great.
Ubuntu Edgy looks also fine.
Xubuntu Edgy doesn't look so cool, but is the system I very much prefer, so I would like to make fonts a little bit more smooth.
Thanks for your help!

---

### Post by stchman on 2007-03-15
> **jmvidalvia said:**
> I have 3 systems in my laptop.
XP looks great.
Ubuntu Edgy looks also fine.
Xubuntu Edgy doesn't look so cool, but is the system I very much prefer, so I would like to make fonts a little bit more smooth.
Thanks for your help!

My fonts look the same.  I will admit XP is prettier than Ubuntu.  XP has a really good looking desktop and fonts.

---

### Post by kerry_s on 2007-03-15
sudo dpkg-reconfigure fontconfig-config

---

### Post by jmvidalvia on 2007-03-15
Already done: no diference.
Used options "native-always-no"
:(

---

### Post by RedSquirrel on 2007-03-15
> **jmvidalvia said:**
> Already done: no diference.
Used options "native-always-no"
:(


I use "autohinter-automatic-no". See my screenshot. I had the same thin-looking fonts you have until I changed from native to autohinter.

And make sure your DPI is set to something reasonable, which I think you've already done (say... 96).
```
xdpyinfo | grep resolution
```

---

### Post by jmvidalvia on 2007-03-16
Hey!
So easy!
Look at my new screenshot.
It doesn't look as nice as XP, but much better than before.
Thank you very much!

---

### Post by yabbadabbadont on 2007-03-16
> **RedSquirrel said:**
> I use "autohinter-automatic-no". See my screenshot. I had the same thin-looking fonts you have until I changed from native to autohinter.

And make sure your DPI is set to something reasonable, which I think you've already done (say... 96).
```
xdpyinfo | grep resolution
```

I always liked that fluxbox theme.  Good choice.  Thanks for the font config information too.

---

### Post by xavier_r on 2007-03-16
Here is my screenshot of Edgy and their fonts... I have changed font rendering and done some other stuff...

if you want something that looks like mine
Follow this guide
[http://www.supriyadisw.net/2006/04/mac-font-on-dapper-drake](http://www.supriyadisw.net/2006/04/mac-font-on-dapper-drake)

---

### Post by RedSquirrel on 2007-03-16
> **jmvidalvia said:**
> Hey!
So easy!
Look at my new screenshot.
It doesn't look as nice as XP, but much better than before.
Thank you very much!

My pleasure. I didn't care for those ugly "thin" fonts either. :)


> **yabbadabbadont said:**
> I always liked that fluxbox theme.  Good choice.  Thanks for the font config information too.

Cheers. I think that *Vista Black* style with the *Human* theme looks very crisp and professional. For quite a while I was trying to find a look that pleased me so I wouldn't feel the need to change it every day. I think I'm satisfied, and it makes my enjoyment of Fluxbox even greater (if that's possible). ;)

---

### Post by yabbadabbadont on 2007-03-16
> **RedSquirrel said:**
> Cheers. I think that *Vista Black* style with the *Human* theme looks very crisp and professional. For quite a while I was trying to find a look that pleased me so I wouldn't feel the need to change it every day. I think I'm satisfied, and it makes my enjoyment of Fluxbox even greater (if that's possible). ;)

I like using Vista Black with the G26 smooth theme.  The only down side is that I had to compile the gtk-smooth-engine from source since edgy doesn't have it for some reason.

---

### Post by RedSquirrel on 2007-03-19
> **yabbadabbadont said:**
> I like using Vista Black with the G26 smooth theme.  The only down side is that I had to compile the gtk-smooth-engine from source since edgy doesn't have it for some reason.

*Use The Source, Luke.* :)

Do you happen to have a screenshot of that theme?

---

### Post by yabbadabbadont on 2007-03-20
> **RedSquirrel said:**
> *Use The Source, Luke.* :)

Do you happen to have a screenshot of that theme?

Here are three.  :D  The first shows the GTK2 version, the second is just eyecandy, and the third shows the GTK1 version.

[[IMG]http://img362.imageshack.us/img362/1315/20070319225250screenud4.th.png[/IMG]](http://img362.imageshack.us/my.php?image=20070319225250screenud4.png) [[IMG]http://img362.imageshack.us/img362/1544/20070319225330screenop3.th.png[/IMG]](http://img362.imageshack.us/my.php?image=20070319225330screenop3.png) [[IMG]http://img120.imageshack.us/img120/8210/20070319225419screenfd7.th.png[/IMG]](http://img120.imageshack.us/my.php?image=20070319225419screenfd7.png)

---

