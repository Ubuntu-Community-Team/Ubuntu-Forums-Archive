---
title: "Use two window managers?"
date: 2007-01-11
forum: Desktop Environments
---

### Post by kapetanski on 2007-01-11
Is it possible to install antoher window manager, so I can use two at the same time, one on each monitor? I'm using xinerama now and I want to change resolution and refresh rate, would also be great to switch one off or so. I'm using xubuntu edgy, so it is possible to install or run another session of xfce on the other screen?

---

### Post by tweedledee on 2007-01-13
> **kapetanski said:**
> Is it possible to install antoher window manager, so I can use two at the same time, one on each monitor? I'm using xinerama now and I want to change resolution and refresh rate, would also be great to switch one off or so. I'm using xubuntu edgy, so it is possible to install or run another session of xfce on the other screen?

To clarify, do you mean you want to run two simultaneous, but independent xfce sessions at once?  Or do you mean you want two window managers at the same (e.g., XFCE's and Fluxbox or something else)?

---

### Post by kapetanski on 2007-01-14
I mean two independent xfce sessions, one on my laptop screen, and the other one on the external monitor. But if that's hard to do, it's fine using fluxbox or any other window manager on one screen.

---

### Post by jem7v on 2007-01-14
Personally, I doubt you can do that.  With a lot of really clever work it might theoretically be Possible, but I have no idea how.

(That's just my guess, though.)

---

### Post by kapetanski on 2007-01-14
I got the idea when I read this at wikipedia: 

Dual display X without Xinerama

It is possible to have a multiple display desktop without using Xinerama. In X terminology, a single X server can support multiple "screens". It is also possible to use separate X servers, and in X terminology this is called using multiple "displays". Both of these methods have been available for a very long time.

With multiple screens (or displays), each physical screen is effectively independent. You can run different window managers, have a different background image, and run different applications on each physical screen.

Some window managers will automatically detect multiple screens, and provide services such as a task bar and window decoration on all screens. This is similar to Xinerama in some ways. However, if your window manager does not do this, you can simply run multiple instances of your window manager, one for each screen.

Some users prefer multiple displays like this, instead of Xinerama. There are many usability advantages to the independence of each screen, compared with Xinerama's method of a single virtual screen stretched over all physical screens.

Some of the advantages: Being sure that new windows always appear on the screen where you launched the application; independent background pictures; independent task bars; notification areas show information about applications associated only with the screen they're on, and so on. All of these are possible with Xinerama too, if they are done by a Xinerama-aware desktop environment with the right features. However, one of the most popular environments, GNOME, although it does have some Xinerama support, is quite poor in the areas described above at the time of writing (GNOME 2.14).

Unfortunately, the independence of each screen (which you get when not using Xinerama) has a noteworthy usability problem: There is no way to move windows between the different screens. A few applications and libraries provide an equivalent behaviour: they can remove their own windows from one screen, and recreate them on the other screen. However, only a few applications can do this, and it's usually difficult to use.

If there was a way to move windows between screens, the behaviour of multiple independent screens would be nearly ideal for many users.

There is one other problem which you are likely to encounter, even if you never want to move windows between screens.

Some applications which open multiple windows, in particular web browsers and certain office applications, must run only once no matter how many separate windows are shown. If you try to run multiple instances of these applications, you will get an error message, or shared state (like bookmarks and cookies in the case of web browsers) may be corrupted or updates lost. But this is exactly what happens when you try to launch these applications on more than one screen at the same time. For example, trying to launch Firefox on two different screens is known to produce an error dialog box, rather than the desirable behaviour which would be to open web browser windows on each screen.

Despite these problems, running multiple independent screens without Xinerama has some advangages, due to limitations with Xinerama (and described in the Known problems section). The relatively independent behaviour of each desktop is one. You can also enable and disable physical screens, or even change the resolution (if XRandR is available) or other display parameters. These are particularly useful features for laptop and tablet PC users who often need to enable and disable an external screen, without affecting the laptop's built-in screen.

from this page: [http://en.wikipedia.org/wiki/Xinerama]("http://en.wikipedia.org/wiki/Xinerama")

---

### Post by tweedledee on 2007-01-16
> **kapetanski said:**
> I got the idea when I read this at wikipedia: 


It sounds to me like it's possible, although from that information I couldn't begin to tell you how to set it up.  However, I interpret that page to suggest that the two screens are kind of like two "desktops" that can't talk to each other - which means they're independent only to a certain extent, you're still really only running one session.  But for what you want, it may not be a big deal.  I suspect all you really need is some setting in X, you probably don't need to install anything else.

---

