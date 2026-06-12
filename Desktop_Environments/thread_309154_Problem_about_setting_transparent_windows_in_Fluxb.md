---
title: "Problem about setting transparent windows in Fluxbox"
date: 2006-11-29
forum: Desktop Environments
---

### Post by tomcheng76 on 2006-11-29
Hi guys,
finally, i chose fluxbox as my second DE. (first is gnome) 
It is great and i love it.
i get my icons, wallpaper, desklets and a transparency rxvt-unicode bg terminal ready
Now. Here comes the problem.
I am able to set the titlebar, menu and split transparency
but i am not able to set the windows frame transparency

I tried to add this code into the theme.cfg, and restarted. 
But it doesnt work
```

toolbar.alpha: 100
window.aplha: 100

```

Can someone tell me how to do it, any help would be appreciated :-D

---

### Post by DJiNN on 2006-11-29
What version of Fluxbox are you using? Is it the one from the Ubuntu Repo's or did you compile it yourself? The reason i ask is because i had a similar problem a while back with the very same thing, (I had compiled Fluxbox myself) and the answer was, when compiling , to enable Transparency as an argumant on the command line. I can't remember exactly what it was that i had to put into the Command Line, but i think that if you go to the Fluxbox homepage it'll mention it there, or read the Docs that come with the Source.

If it's from the Repo's then i'm not really sure what it is. Please post when you get the answer though, as it may help someone else in the future. :)

---

### Post by tomcheng76 on 2006-11-29
Thanks for the quick reply
fluxbox was installed from repo.
I just tried to edit the entry session.forcePseudoTransparency to true in ~/.fluxbox/init
But it doesnt help.
```

bomber@ubuntu:~$ fluxbox -i
Fluxbox version: 1.0rc2
Compiled: Sep 28 2006 15:19:57
Compiler: GCC
Compiler version: 4.1.2 20060920 (prerelease) (Ubuntu 4.1.1-13ubuntu3)

Defaults:
    menu: /etc/X11/fluxbox/fluxbox.menu-user
   style: /usr/share/fluxbox/styles/Clean
    keys: /etc/X11/fluxbox/keys
    init: /etc/X11/fluxbox/init
    nls: /usr/share/fluxbox/nls

Compiled options (- => disabled): 
-DEBUG
EWMH
GNOME
-IMLIB2
KDE
NLS
REMEMBER
RENDER
SHAPE
SLIT
TOOLBAR
XFT
XINERAMA
XMB
XPM

```
Here is the problem snapshot.
[[IMG]http://img451.imageshack.us/img451/9366/screenshot2006112921070ef7.th.png[/IMG]](http://img451.imageshack.us/my.php?image=screenshot2006112921070ef7.png)

---

### Post by DJiNN on 2006-11-29
> **tomcheng76 said:**
> Thanks for the quick reply

You're very welcome. :)

> fluxbox was installed from repo.
I just tried to edit the entry session.forcePseudoTransparency to true in ~/.fluxbox/init
But it doesnt help.

I think it's more than that. Have you looked at [this]("http://ubuntuforums.org/showthread.php?t=200153&highlight=fluxbox+transparency") thread? I remember it having something to do with Xrender, being both enabled in X & also in Fluxbox. Also, you have to be using something like fbsetbg to change the backgrounds & to have Transparency.  Also, i seem to remember turning "Xinerama" OFF for some reason..... something to do with NOT having Dual Monitors i think. 

Having said all this, i did manage to get it working but that was on Dapper. I haven't tried it on Edgy yet, and i probably won't for some time. (Too busy doing other stuff.) :)

But have a look and see if that thread helps. Please let me know how you get on, and by the way, that's a great looking desktop. Are you using "Adesklets"?

DJiNN

---

### Post by tomcheng76 on 2006-11-30
Yeah! It is adesklet 
i just added gkrellm - the most complete system monitor on my desktop
i am going to compile my fluxbox now
just want to know, 
should i use apt-get --purge remove fluxbox first before complie my own fluxbox?
i will keep those configuration files in ~/.fluxbox first for sure
Thanks guys, here is my new snapshot :)
[[IMG]http://img182.imageshack.us/img182/7130/screenshot2006113018544ft9.th.png[/IMG]](http://img182.imageshack.us/my.php?image=screenshot2006113018544ft9.png)

---

### Post by DJiNN on 2006-12-01
> **tomcheng76 said:**
> Yeah! It is adesklet 
i just added gkrellm - the most complete system monitor on my desktop 

Looks good. GkrellM is really good isn't it? Been using it here for a while. 

> i am going to compile my fluxbox now
just want to know, 
should i use apt-get --purge remove fluxbox first before complie my own fluxbox?

Well, i'm not sure if it's needed, but i guess it wouldn't hurt. :)

> i will keep those configuration files in ~/.fluxbox first for sure
Thanks guys, here is my new snapshot :) 

Always worth keeping backups of everything, even if it doesn't get used in the end. :)  Nice looking desktop though. Love the transparent Terminal..... how did you get that?

Please post your results when you get the time. Always good to hear how it's going. :)

DJiNN

---

### Post by BLTicklemonster on 2006-12-01
> **tomcheng76 said:**
> Yeah! It is adesklet 
i just added gkrellm - the most complete system monitor on my desktop
i am going to compile my fluxbox now
just want to know, 
should i use apt-get --purge remove fluxbox first before complie my own fluxbox?
i will keep those configuration files in ~/.fluxbox first for sure
Thanks guys, here is my new snapshot :)
[[IMG]http://img182.imageshack.us/img182/7130/screenshot2006113018544ft9.th.png[/IMG]](http://img182.imageshack.us/my.php?image=screenshot2006113018544ft9.png)

I think that's about the sexiest desktop I've ever seen.

I'm using fluxbox and this thread has piqued my interest. One thing, though.

What is the slit, where is it, what does it do, how do I access it, what are it's benefits?

---

### Post by DJiNN on 2006-12-02
> **BLTicklemonster said:**
> 
What is the slit, where is it, what does it do, how do I access it, what are it's benefits?

I've never quite worked out how the Slit works, or what it does either? Any long time Fluxbox users out there (bodhi?) care to enlighten us on this one?  

I do know that a lot of people really like using the slit, which i think is some sort of place for "Dockable" apps to sit, but that's just a guess. Hopefully someone will come along & put us right? :)

DJiNN

---

### Post by RedSquirrel on 2007-01-07
> **DJiNN said:**
> I've never quite worked out how the Slit works, or what it does either? Any long time Fluxbox users out there (bodhi?) care to enlighten us on this one?  

I do know that a lot of people really like using the slit, which i think is some sort of place for "Dockable" apps to sit, but that's just a guess. Hopefully someone will come along & put us right? :)

DJiNN


You're right. The slit holds WindowMaker dockapps, and anything that can be run in "withdrawn" mode.

If there are no apps running in your slit, then the slit is invisible.

If you want to see something running in the slit, try some of the dockapps in the repositories, or at [dockapps.org]("http://www.dockapps.org/"). You can run them from the terminal:

```
wmmatrix &
```Or, you can put them in your ~/.fluxbox/startup file so that they will be there every time you start Fluxbox.

The wmmatrix app puts a small window with Matrix-like code in it (like the xscreensaver "xmatrix").

The slit can be placed on any border of the screen (e.g., right-center, top-center, and so on).

Anyway, those are just a few details.

Here is a link to the documentation on the slit from the Fluxbox website:

[http://fluxbox.sourceforge.net/docbook/en/html/chap-slit.html](http://fluxbox.sourceforge.net/docbook/en/html/chap-slit.html)

It's actually a nice feature which I have experimented with in the past, but I generally prefer an uncluttered desktop, so I don't have any apps running there now.

By the way, have you ever had the problem of maximizing a window and seeing a few pixels of empty space on the right edge of the screen? I had this when I first installed Fluxbox. Well, there is an empty slit sitting there. You can fix this by going into your menu as follows:

Menu -> Configure -> Slit 

and toggling "Maximize Over"

The Fluxbox Wiki has a good FAQ section:

[http://fluxbox-wiki.org/index.php/Faqs](http://fluxbox-wiki.org/index.php/Faqs)

---

### Post by heathen on 2007-01-12
did you ever work this out? I'm having the same issue

---

### Post by RedSquirrel on 2007-04-15
OK, this is an old thread, but I remember reading it a while ago and wondering how to make windows transparent...

To the best of my knowledge, it isn't possible to have transparent windows using Fluxbox settings alone. You would need to install xcompmgr and transset. They are both in the repos. I have found them to be slow, however, especially on old hardware.

---

