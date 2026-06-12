---
title: "I Don't Really Understand Desktops..."
date: 2006-08-03
forum: Desktop Environments
---

### Post by ubernatural on 2006-08-03
So I installed Ubuntu, which comes with a nice Gnome desktop.  Heard about Xubuntu and was curious, so I used Synaptic to grab xubuntu-desktop.  Logged out, switched to that session, and saw the nice new UI.  I know there's more to it than just the looks, but I can't quite understand it at the moment.  Here's my understanding which is incomplete:

1. The core of ubuntu is pretty much the same no matter what desktop I'm using.
2. Different desktops seem to come with their own bunch of preferred applications that get installed.  For example, now I see Xfmedia in my applications menu, since installing xubuntu-desktop.  In this way, a desktop is a bit like a Linux distribution(?)
3. Desktops have their own windowing APIs(?).  xubuntu prefers GTK applications, and I guess Gnome and KDE have their own windowing APIs as well.
4. Even if I am running xubuntu, I can still run apps that use other APIs.  For example, my nice gnome-system-monitor still works fine inside xubuntu.  I guess this is because I have all of the libraries installed already that support the Gnome windowing API(?).
5. I get the performance benefits of xubuntu so long as I don't launch any Gnome (or KDE) apps(?)

Sorry for the multi-question post.  Could probably be quickly answered with a link to an article or FAQ describing in detail what exactly a desktop environment is all about.

Thanks

---

### Post by wylfing on 2006-08-03
You are very perceptive. Basically, all your assumptions are correct. You can definitely run applications that require different APIs -- you just have to download and install those APIs, and "suffer" the overhead of loading them at runtime.

---

### Post by 23meg on 2006-08-03
> 3. Desktops have their own windowing APIs(?). xubuntu prefers GTK applications, and I guess Gnome and KDE have their own windowing APIs as well.GNOME and XFCE use GTK+ whereas KDE uses QT.
> 
5. I get the performance benefits of xubuntu so long as I don't launch any Gnome (or KDE) apps(?)More true with KDE apps, since you need to load the QT libs.

---

### Post by wylfing on 2006-08-03
Roger what 23meg said. There is very easy portability between Gnome and XFCE desktops. It gets *slightly* more difficult when you want to run Qt apps, but even that is not a big deal.

---

### Post by asplode on 2006-08-03
Its as difficult as having synaptic automatically download the necessary libraries and dependencies for you when you pick the program you want, ala Amarok

---

### Post by ubernatural on 2006-08-03
Thanks for the insights folks.  Is there any way of knowing what API a certain application uses (aside from those applications prefixed with gnome- or somesuch)?  For example, if I want to run a console program in xubuntu, would it be more overhead to use a kde console rather than a gtk console (if one exists)?  I may be splitting hairs here, but I'm curious nonetheless.

Also curious about non-UI applications.  If I have some processes running without UI, will these applications possibly require a Windowing API like GTK or QT?  Perhaps only those applications with a UI will depend on a particular Windowing API?

One final question, are there any other popular windowing apis (libraries?) besides GTK and QT?

Thanks again for the responses.

---

### Post by 23meg on 2006-08-03
You should mind the fact that the QT libraries will take quite a bit of extra RAM when loaded though.

---

### Post by carlosqueso on 2006-08-03
Usually, if an app's name starts with g, it is GTK and if it starts with either k or qt, it's QT.  Also, you can read the descriptions in synaptic for clues.  Pretty much anything in the default Ubuntu installation uses GTK.  

If you arent' using anything with graphics or buttons, you aren't using GTK or QT.  Non-UI and console apps don't use either (although some console apps use ncurses, which is kind of a text-based fake GUI).

As far as the console question, yes, but most are based on xterm, which if I understand correctly, doesn't use either.

[http://en.wikipedia.org/wiki/Widget_toolkit](http://en.wikipedia.org/wiki/Widget_toolkit)  has more info on this.  I've heard of linux software being writen with Tk and FLTK, and Firefox uses it's own thing called (I believe) XUL.

---

### Post by cptnapalm on 2006-08-03
ubernatural: are there any other popular windowing apis (libraries?) besides GTK and QT?

These days, it is mostly GTK and QT.

A long time ago, there was Motif.  Tcl/Tck was widely used.  Both were pretty... ugly.

A few years ago, there was the Wings library, which was Window Maker's.  Window Maker was, for a long time, a very popular, lightweight and attractive window manager.  Though in the Ubuntu repositories (universe I think), it definitely seems to have fallen out of popular favor.  It had a massive number of handy little dock apps, aeons ago.  Based on the NeXTStep gui, it was quite nice for its day.

---

### Post by 23meg on 2006-08-04
WxWidgets is also very popular, but isn't precisely a widget toolkit in itself, it's an abstraction method that calls widgets of certain types that are native to the platform the app is running on. This makes multiplaftorm development much less painful. 

Some applications (very rarely) also use xlib directly rather than resorting to widget toolkits.

---

