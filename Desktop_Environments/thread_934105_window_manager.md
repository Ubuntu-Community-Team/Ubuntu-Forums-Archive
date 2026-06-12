---
title: "window manager"
date: 2008-09-30
forum: Desktop Environments
---

### Post by nzadLithium on 2008-09-30
Hey, I have a pentium 2 with a nvidia riva tnt2 gfx card in it doing absolutely nothing. So what i decided to do was use it as my kind of toying round with linux machine :D

I've loaded it up with crux linux (may not have been the best idea as it seems to take 4 hours to compile glib :D ). Now i've got a web browser on it (Dillo) and the nvidia drivers setup, i'm wondering what extremely lightweight window manager i can stick on it. I've been looking at icewm, it looks great, but i'm wondering if there's anything more lightweight that anyone knows of?

Pretty much i'm looking for the lowest ram using, fastest possibly window manager, that has desktop icons, and a title bar (with close, maximise, minimise buttons on it and the ability to move windows around on the screen :D). I don't really need any panels or menu's but if whatever anyone thinks of has them I don't mind (as long as it goes faster than icewm :D ) Oh, and if looks like its been made in dos or something i don't care as long as it works :)

TY :)

---

### Post by atitupan1 on 2008-09-30
Hi,
I have Pentium2 and had installed Linux as operating systems but know I am looking for the lowest ram using fastest window manager.

___________________________________________________________-

[Houston Gift Shop](http://www.florist-flowers-roses-delivery.com/texas/houston_tx.html) [loans with no credit check](http://www.cheaponline-loans.co.uk/help/no-credit-check-loans.php) [pisos vilafranca](http://www.vilafrancadelpenedes.com/-1/posts/1_Habitatge/0/) [download iPhone ringtones](http://www.myringtoneshub.com/specials/buy-cell-phone-ringtones.htm)

---

### Post by Rumplesmigskin on 2008-09-30
[DWM]("http://suckless.org/wiki/dwm") is a good choice. It's plain C code, and fast as hell. There is a version in the repositories, but you're better off installing from source. Other window managers that would be good for your purposes would include:
- WMII (same website as above, less compiling needed. I like it better.)
- EvilWM
- StumpWM (if you like lisp)
- Fluxbox (purty)
- Blackbox (also purty)
- Openbox (not so purty, but works)
- XFCE (it's more of a desktop environment than a window manager, but it's fast)
- IceWM (very much like windows 95, and is good and snappy)

Fire up synaptic and search for "window manager" and you should find plenty more.

EDIT: If you really want to minimise RAM usage, remove gdm/kdm, log into console mode, put the window manager you want into your ~/.xinitrc and run startx. No login manager required, should save a few MB.

---

### Post by kerry_s on 2008-09-30
i don't think any wm has desktop icons, you'll have to use a separate program for that.

can you give your specs, as in ?mhz and ?mb ram

there so much to choose from, but you really got to be detailed for any 1 to recommend stuff that actually works on your system.

anyways, i vote jwm+rox, that will give you a window manager and a file manager that can also do desktop icons.

---

### Post by nzadLithium on 2008-09-30
Well i found a great one, its so minimal it took like 2 minutes to compile :D
[http://nickgravgaard.com/windowlab/](http://nickgravgaard.com/windowlab/)

CPU:
267MHz Pentium 2 (Klamath)
512kb lvl2 cache

I think it has 128Mb of ram.

So what do I do about icons then? perhaps you list some commonly used desktop icon programs?

And also the distro that I have (for the pentium 2) opens 3 copies of xterm by default upon starting up the xserver. Once i start the window manager, I tried closing one, and it just locked up the whole xserver, the mouse could move, but that was it. Any idea's whats going on there? (I couldn't ctrl + alt + f2 or anything, although its my understanding that i need to install another program for that functionality as well?)

TY :)

---

### Post by kerry_s on 2008-09-30
have you tried dsl linux it's built for those kind of specs.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

> And also the distro that I have (for the pentium 2) opens 3 copies of xterm by default upon starting up the xserver. Once i start the window manager, I tried closing one, and it just locked up the whole xserver, the mouse could move, but that was it. Any idea's whats going on there? (I couldn't ctrl + alt + f2 or anything, although its my understanding that i need to install another program for that functionality as well?)


do you have swap? that sometimes happens when you run out of memory. you want at least 512mb swap, 1gig swap would be even better if you can spare the space.

---

### Post by nzadLithium on 2008-10-01
I do have swap. 2gb of it (had an old spare hard disk, so i just wiped the whole thing and am using as swap :D ).

Well I did start writing about what I liked about Crux, over DSL but then i realised it was gonna end up being a massive post about my dislikes of DSL and what i find great about crux. So I deleted it :p Basically what I dislike about dsl, is the package management system. (Which is what I like about crux :D )

Basically, I spent about a month deciding what distro I wanted on it, it took me about two hours to get my list down to 5 distro's then I decided to wait till end of broadband month so the download didnt take a chunk out of my cap :D By the end of the month I had decided on two to try, Deli Linux, and Crux Linux. I downloaded them both, burnt the iso's Deli didn't boot, so i used Crux :D

Crux seems great to me, so I want to stick with it.

So what programs do I need to install to get desktop icons (which I'm not actually sure whether I want or not now :p ).
And what program do I need to install to get ctrl + alt + f2 to switch to a terminal :D

TY

---

### Post by joseph2008 on 2008-10-01
A window manager is computer software that controls the placement and appearance of windows within a windowing system in a graphical user interface. 
_______________________________________________________________
[promotional items](http://www.ideasbynet.com/promotional-items.htm) [Tail Lights](http://www.andysautosport.com/euro_tail_lights.html) [perfume store](http://www.eperfumestore.com/) [Sexual Predator List](http://www.registeredsexualpredators.org)

---

### Post by mali2297 on 2008-10-01
Another CRUX user here! :-)

If you want to know about other available window managers, this is a great resource:
[http://www.gilesorr.com/wm/index.html](http://www.gilesorr.com/wm/index.html)

> **nzadLithium said:**
> 
So what do I do about icons then? perhaps you list some commonly used desktop icon programs?


[list]
[*][Idesk]("http://idesk.sourceforge.net/wiki/index.php/Main_Page").
[*][DeskLaunch]("http://www.oroborus.org/").
[/list]
> 
And also the distro that I have (for the pentium 2) opens 3 copies of xterm by default upon starting up the xserver. 

That is specified in /usr/lib/X11/xinit/xinitrc (if you're using startx and not a login manager). Create your own .xinitrc file in your home directory to override it.

> **nzadLithium said:**
> 
And what program do I need to install to get ctrl + alt + f2 to switch to a terminal :D

That's a built in feature of X. My guess is that there is something wrong with the key bindings. Does Ctrl, Alt and F2 work for other tasks?

---

### Post by nzadLithium on 2008-10-01
ah thx so much mali. This should fix all my problems, except possibly the keybindings (lets see xterm screw up the xserver if it never starts up :D ).

I'll have to test out the key bindings tomorrow, as i just shutdown the other pc and it takes like 8 minutes to get it fully started up :D

---

### Post by Sycron on 2008-10-01
Well i always liked openbox and fluxbox.

---

### Post by nzadLithium on 2008-10-01
keybindings work perfectly fine as long as i don't close xterm, the second i close xterm the whole machine pretty much locks up, only the mouse can move. :S

I got desklaunch, it seems to work fine, but it does something weird, probly something to do with the window manager, but basically, the icons for desklaunch are inside a window making it more like a dock :D It still works though so i'm happy :)

I commented out two of the xterms so now it only loads one, I'll get rid of this one later, once i'm happy thats everything is setup nice :)

One last question, how do i get a desktop background? :D

---

### Post by tuvw962 on 2008-10-02
A young Irish girl goes into her priest on Saturday morning for confession."Father, forgive me for I have Thinned.""You've Thinned?"[wow gold](http://www.mmoinn.com)"Yes, I went out with me boyfriend Friday night. He held me hand twice, kissed me three times, and made love to me two times.""Daughter! I want you to go straight home, squeeze seven lemons into a glass, and drink it straight down.""Will that wash away me Thin?""No, but it will get the silly smile off your face." [warhammer gold](http://www.gold-warhammer.com/) [world of warcraft gold](http://www.mmoinn.com/) [wow power leveling](http://www.mmoinn.com/mmoinn_pl/)[http://www.mmoinn.com](http://www.mmoinn.com/)

---

### Post by mali2297 on 2008-10-02
> **nzadLithium said:**
> keybindings work perfectly fine as long as i don't close xterm, the second i close xterm the whole machine pretty much locks up, only the mouse can move. :S

That's strange. Have you tried making your own .xinitrc?

> 
I got desklaunch, it seems to work fine, but it does something weird, probly something to do with the window manager, but basically, the icons for desklaunch are inside a window making it more like a dock :D It still works though so i'm happy :)

I think idesk is more popular, did you try it?

If you're happy with a dock, you can also try [wbar]("http://freshmeat.net/projects/wbar/").

> 
One last question, how do i get a desktop background? :D

There are many apps that can do this. I use the image viewer feh.

A sample .xinitrc file:
```

feh --bg-center /path/to/picture.jpg &
desklaunch &
exec windowlab

```

---

### Post by Harii on 2008-10-03
I use Oroborus--
its lite and can use xfwm4(xfce)themes.
[IMG]http://photos-485.ll.facebook.com/photos-ll-sf2p/v362/132/113/1184812485/n1184812485_30184198_6559.jpg[/IMG]
i use an tablaunch-myGtkMenu for an menu system.
i could never get deskmenu to work right.

---

### Post by kerry_s on 2008-10-03
very nice, hey whats that window theme called, i been looking for the gnome version, but couldn't remember the name.

---

### Post by mali2297 on 2008-10-04
> **Harii said:**
> I use Oroborus--
its lite and can use xfwm4(xfce)themes.

i use an tablaunch-myGtkMenu for an menu system.
i could never get deskmenu to work right.

That looks really nice. I guess you have conky running as well?

---

### Post by Harii on 2008-10-04
that is conky at the bottom and that theme is called "Elberg_green".
i mess up and posted a screenshot of an oroborus-most wm have it.
I have other screenshots that do have xfce themes at this url:

[http://www.facebook.com/album.php?page=2&aid=2001933&l=56aa3&id=1184812485]("http://www.facebook.com/album.php?page=2&aid=2001933&l=56aa3&id=1184812485")

To use xfce themes you need to take the theme out of the "xfwm4 folder" to get it to work. It will not look into the folder.

---

### Post by kerry_s on 2008-10-05
> **Harii said:**
> that is conky at the bottom and that theme is called "Elberg_green".
i mess up and posted a screenshot of an oroborus-most wm have it.
I have other screenshots that do have xfce themes at this url:

[http://www.facebook.com/album.php?page=2&aid=2001933&l=56aa3&id=1184812485]("http://www.facebook.com/album.php?page=2&aid=2001933&l=56aa3&id=1184812485")

To use xfce themes you need to take the theme out of the "xfwm4 folder" to get it to work. It will not look into the folder.

thanks! the name made it so easy to find: [http://themes.freshmeat.net/search/?q=elberg&section=projects&Go.x=0&Go.y=0](http://themes.freshmeat.net/search/?q=elberg&section=projects&Go.x=0&Go.y=0)

---

### Post by ricky045 on 2008-10-11
One of the guiding philosophies of The X Window System (and also UNIX itself) is that its functionality is achieved through the co-operation of separate components, rather than everything being entwined in one huge mass (or should that be mess?). The advantage of this is that a particular part of the system can be changed simply by replacing the relevant component. The best example of this is the concept of a window manager which is essentially the component which controls the appearance of windows and provides the means by which the user can interact with them. Virtually everything which appears on the screen in X is in a window, and a window manager quite simply manages them.
=================================
ricky045
[LA Flowers](http://www.florist-flowers-roses-delivery.com/california/los_angeles_ca.html)

---

### Post by nzadLithium on 2008-10-11
thx guys your help is much appreciated all sorted now (I hope) :D

---

