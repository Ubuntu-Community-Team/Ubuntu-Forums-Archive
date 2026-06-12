---
title: "This is why we newbs don't know the difference between WM and DE!"
date: 2008-02-14
forum: Desktop Environments
---

### Post by Pogeymanz on 2008-02-14
Because distros don't advertise them equally! Ubuntu always says it uses Gnome, but it could say "Uses gnome + metacity"

So, I have some questions:
Fluxbuntu uses fluxbox. Is fluxbox a WM or DE? If it's a WM, then what is the DE for fluxbuntu?

Puppy Linux and DSL use JWM. So what's the DE?

What is the WM for Kubuntu?

What the heck is E17? DE? WM? Both?

Are panels part of the DE or WM?

Pretend I am sitting here staring at my workspace with a few windows open. What is being controlled by the WM and what is being controlled by the DE?

---

### Post by chipants on 2008-02-15
well, there's a fine line tread between window managers (WM) and desktop environments (DE). while every DE needs a window manager, not all window managers encompass a complex DE.

essentially, a window manager is just that... something that manages windows. specifically, placement of windows, theming, etc.

a desktop environment needs a window manager, but provides additional tools to form a comprehensive work environment. for example, tools that provide a common interface for applications to communicate like a clipboard, panels, 'start'-type menus, etc.

Kubuntu uses the KDE desktop environment, which uses its own KWin window manager.

Enlightenment is kind of an interesting situation. (you mentioned E17) Enlightenment actually started out as gnome's window manager many years ago, but eventually split off of the gnome project, adding features, eventually becoming a light DE in its own right.

fluxbox, is basically a window manager, but can be considered a VERY light DE considering the additional features provided beyond just managing windows.

so window managers provide a dock-type tool, but mostly DEs take care of that.

hopefully, that answers your question.

---

### Post by Pogeymanz on 2008-02-15
So does that mean that someone might run Gnome and Fluxbox and someone else might have only fluxbox?

Thank you for clearing that up.

---

### Post by chipants on 2008-02-15
yes! actually, you *can* fun fluxbox (instead of metacity) as gnome's WM.

conversely, you can run fluxbox entirely on its own. as a matter of fact, i often run fluxbox on its own.

---

### Post by cknight on 2008-02-15
> **chipants said:**
> yes! actually, you *can* fun fluxbox (instead of metacity) as gnome's WM.

conversely, you can run fluxbox entirely on its own. as a matter of fact, i often run fluxbox on its own.
Most users of Fluxbox run it on its own.  I'm amused by the idea of running it with Gnome.  How well do they mesh?

---

### Post by farruinn on 2008-02-15
> **EmosSuck777 said:**
> What the heck is E17? DE? WM? Both?

Are panels part of the DE or WM?

Pretend I am sitting here staring at my workspace with a few windows open. What is being controlled by the WM and what is being controlled by the DE?

I think E17 are calling themselves a "desktop shell". It's primarily a window manager but with some added features.

For the most part, panels are part of the DE (such as gnome-panel) but E17, while primarily a WM also provides some panel-like thingies (I don't remember what they're calling them).

Usually, the window manager just controls what your window borders look like and how your windows behave. More than that and it's usually not the WM anymore.

---

### Post by RedSquirrel on 2008-02-15
> **EmosSuck777 said:**
> Are panels part of the DE or WM?

Sometimes neither. There are panels which are entirely separate, small applications. An example is fbpanel, which is the one I'm using right now (with the Openbox WM). fbpanel is not "part of" any DE or WM. ;)

[http://fbpanel.sourceforge.net/](http://fbpanel.sourceforge.net/)

... and that's just one example. There are lots of other panels out there...

---

### Post by hgurol on 2008-02-15
Hmmm, so Metacity is the windows manager of Gnome, right? I thought it was the Nautilus that is WM for Gnome ?

Is there any visual sign that I can say "Oh, this is the Metacity part/section of Gnome" while using my laptop?

I know thats a stupid question but I, even myself, cant believe that Im confusing these small and simple things, sorry...

---

### Post by LaRoza on 2008-02-15
> **hgurol said:**
> Hmmm, so Metacity is the windows manager of Gnome, right? I thought it was the Nautilus that is WM for Gnome ?

Is there any visual sign that I can say "Oh, this is the Metacity part/section of Gnome" while using my laptop?

I know thats a stupid question but I, even myself, cant believe that Im confusing these small and simple things, sorry...

No, GNOME on Ubuntu uses Compiz or Metacity as the Windows Manager.

The File Manager is Nautilus.

---

### Post by Nythain on 2008-02-15
Nautilus also manages the desktop in gnome... wich will lead to minor complications running fluxbox within gnome from what i've gathered, i dont know for sure, because i run flux by itself (well, with X, but hey, who's counting) and Gnome with metacity (well, technically compiz, but with the option allowing metacity to still control things, instead of emerald)

---

### Post by urukrama on 2008-02-15
> **Nythain said:**
> Nautilus also manages the desktop in gnome... wich will lead to minor complications running fluxbox within gnome from what i've gathered, i dont know for sure, because i run flux by itself (well, with X, but hey, who's counting) and Gnome with metacity (well, technically compiz, but with the option allowing metacity to still control things, instead of emerald)

Nautilus does not interfere with Fluxbox or Openbox if you just want these window managers to manage the windows. If you would like to use the Openbox/Fluxbox menu, though, you will have to disable Nautilus' control over the desktop.

---

### Post by smartboyathome on 2008-02-17
E17 is a window manager, but has featurew which include a desktop, shelves (the equivilent of GNOME panels, but not able to run by themselves), and modules to give E17 extra features.

---

### Post by kaiju on 2008-02-17
i suspect that none of the widely used wm's are just purely window managers.
e.g. fluxbox (like all the *box wm's for that matter, i think) also has support for custom keybindings, and offers a menu as well as a panel with notification area and workspace switcher.
or, as smartboyathome said, enlightenment is another feature-rich wm (just take a look into its grid of virtual desktops).
and on top of that, most wm's can use different modules for added functionality, so i'd think there is an important difference between window managers like metacity and window managers like openbox, while the divide between the latter wm's (that can be used by themselves) and full de's (e.g. gnome or kde) is not so big at all.

---

