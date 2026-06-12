---
title: "Kwin vs Compiz (sorta)"
date: 2010-04-21
forum: Desktop Environments
---

### Post by keljaden on 2010-04-21
Okay, I know in gnome I use compiz, but KDE has Kwin.  In addition to having pretty much the same desktop effects as compiz, does Kwin also use the GPU to render and run DE as opposed to it being CPU.  I have read articles giving me convoluted information on this and I want to have this down.

How do Kwin and Compiz differ/whats the same?  (both technical code/hardware usage wise, and effects).

Also, whats this beryl thing?  From my understanding on it, the beryl peeps just gave up and started to work making compiz better.

---

### Post by lovinglinux on 2010-04-21
> **keljaden said:**
> How do Kwin and Compiz differ/whats the same?  (both technical code/hardware usage wise, and effects).

I couldn't think about living without Compiz, which made me switch to KDE before Gnome 3 ruins my life. Now I'm using Kwin and I couldn't be happier. It is a lot simpler to configure than Compiz and has all the effects I need (related to productivity). For instance, you can change a lot of window options from the window itself, while in Compiz I had to open the settings manager and go through several options in the Window Rule, Place and Scale plugins.

> **keljaden said:**
> Also, whats this beryl thing?  From my understanding on it, the beryl peeps just gave up and started to work making compiz better.

Beryl was a fork of Compiz that has been re-merged with it to form Compiz Fusion. See [http://en.wikipedia.org/wiki/Beryl_%28window_manager%29](http://en.wikipedia.org/wiki/Beryl_%28window_manager%29)

---

### Post by keljaden on 2010-04-21
so what makes Kwin different than compiz other than a different settings manager? Does Kwin still use the GPU for all the effects as opposed to the CPU?

---

### Post by Zorael on 2010-04-22
A **window manager** handles windows. It decides which window has focus, moves them around, resizes them, minimizes/maximizes, etc.

A **window decorator** draws decorations (borders and titlebars including buttons) around windows.

A **window compositor** adds a buffering layer to which applications write, including the window manager and decorator. Their output may then be transformed before it is showed on the screen. This is where the cubes, expose effects, scaling, transparency, contorting, etc comes in.

**Compiz** is a window manager and a window compositor, but it needs a window decorator to work. Else you'll end up with no window borders; just search the forums and see how many hits 'compiz window borders' has. The compiz-gnome package I believe comes with a decorator that's compatible with the normal GNOME window themes. **Emerald** is an alternative decorator but it uses its own themes. I don't know if compiz-kde is around anymore, but it used to come with **kde-window-decorator**, which is/was a buggy/completely broken decorator compatible with KWin themes.

**Metacity** is GNOME's standard window manager and decorator. It has no compositing abilities so no 3D effects.

**KWin** is the KDE window manager decorator and compositor. The compositing features can be turned on and off, in System Settings -> Desktop -> Desktop Effects and via the Alt+Shift+F12 hotkey.

As lovinglinux noted, **Beryl** was a fork of Compiz. Old and superseded.

I don't know exactly how Compiz relates to **Compiz Fusion** anymore. It used to be that Fusion was Compiz with extra plugins (largely ported from Beryl when merging the projects), but then there was an effort to make it all just Compiz again, and now I remember reading an announcement that they want to develop them separately again.

---

### Post by 3Miro on 2010-04-22
KDE Settings Manager -> Desktop you can change all the Kwin options and settings.

Kwin - composition = CPU rendering, i.e. very simple.

Kwin + composition = GPU rendering and the ability to use effects.

Kwin and Compiz may use similar libraries and methodology, but Kwin is specifically build for KDE and has abilities that compiz can never have (such as preview of minimized windows). Kwin is also smoother and takes less resources. Compiz is basically a hack on top of whatever environment it is sitting on, a beautiful hack, but a hack never the less.

Kwin has most of the same effects as Compiz.

---

### Post by c00lwaterz on 2010-04-22
interesting. can kwins run on gnome?

---

### Post by 3Miro on 2010-04-22
> **c00lwaterz said:**
> interesting. can kwins run on gnome?

I don't think so, you can try:
```
sudo apt-get install kubuntu-desktop
```
to install KDE and Kwin and then
```
kwin --replace
```
but I don't think it will work. In any case, under Gnome you will be better off with compiz, since unlike kwin it was build to service Gnome.

---

### Post by Zorael on 2010-04-22
In case you don't want to pull the whole Kubuntu distro, KWin is in the **kde-window-manager** package. Installing it will pull the basic KDE libraries as dependencies but leave out Kubuntu art and default apps.

---

### Post by SmSpillaz on 2010-04-23
> **3Miro said:**
> KDE Settings Manager -> Desktop you can change all the Kwin options and settings.

Kwin - composition = CPU rendering, i.e. very simple.

Kwin + composition = GPU rendering and the ability to use effects.

Kwin and Compiz may use similar libraries and methodology, but Kwin is specifically build for KDE and has abilities that compiz can never have (such as preview of minimized windows).



Wrong. It's possible to implement this in compiz (I've done it), but we don't implement it because it breaks minimization. I believe KWin also removed it for this reason

> 

 Kwin is also smoother and takes less resources. Compiz is basically a hack on top of whatever environment it is sitting on, a beautiful hack, but a hack never the less.



KWin is a window manager. Compiz is a window manager. I don't see how either of them could fit into the category of being a "hack".

Both of them follow EWMH, which is the freedesktop.org spec on how a window manager should work. Window managers are not supposed to be built around the desktop environment - they can certainly use some shared libraries that the desktop environment uses, but in order to follow any standards they need to use window hints as per EWMH.

In fact, KWin uses X11 window properties (something you are supposed to use in EWMH) to implement functionality like thumbnails in the plasma taskbar (or the 'slide' effect on menus). All they do is define the properties of the effect and it's up to the compositor to implement it. In fact, we implement them all really trivially in compiz already.

> 
Kwin has most of the same effects as Compiz.

It is true that KWin is catching up and probably has 80% feature parity, but the implementation details are far different and there are certain things that KWin wont implement.

---

### Post by krazyd on 2010-04-23
> **SmSpillaz said:**
> Wrong. It's possible to implement this in compiz (I've done it), but we don't implement it because it breaks minimization. I believe KWin also removed it for this reason
Nope, kwin has this.
edit: I may have misunderstood 3Miro's statement. What I mean is that kwin caches the window state at the time of minimisation to provide previews. It doesn't continue rendering to a minimised window's pixmap.

> **SmSpillaz said:**
> It is true that KWin is catching up and probably has 80% feature parity, but the implementation details are far different and there are certain things that KWin wont implement.

I'm intrigued.. what are these features?

---

### Post by keljaden on 2010-04-23
Kwin has wobbly windows (which wobble nicer)
I like how the cube is done for when I am using my Desktop machine, but when using the laptop, I miss the ctrl+alt+rightarror to switch cube, but as I recall, that is being fixed in the next release of kubuntu (and hopefully kept with Linux mint 9 KDE as their 64 bit custom flash support is the best in linux).

But the effects that follow around the cursor in Kwin look like crap, they don't have a pretty "draw with fire" either.

and You can't make it rain, only snow.

I have also noticed that Compiz has REDUCED the amount of effects in the past year.  I used to be able to have an aquarium inside my cube...for reasons I cannot fathom, they removed it.

also, if I have wobbly windows on in Kwin, can I assume I have Kwin+composition?

How did he get the windows to all float around in the backround and what did he use for screen capture. I have not seen ANY of these effects available in compiz-fuzion last release...[http://www.youtube.com/watch?v=Y4wB3GUemVw&feature=related](http://www.youtube.com/watch?v=Y4wB3GUemVw&feature=related)

IMO, I think beryl by itself was ten times better than compiz is right now...example
[http://www.youtube.com/watch?v=kYgV2GlsufI&feature=related](http://www.youtube.com/watch?v=kYgV2GlsufI&feature=related)
Look how epic that is!!! I want that!

Also anyone see [http://www.sun.com/software/looking_glass/](http://www.sun.com/software/looking_glass/) before?  Its a 3D DE from what I can tell...I like sun so much, first virtualbox, now this. kudos to those devs.

And thanks everyone for you replies so far!

---

### Post by Zorael on 2010-04-23
> **SmSpillaz said:**
> Wrong. It's possible to implement this in compiz (I've done it), but we don't implement it because it breaks minimization. I believe KWin also removed it for this reason

It's left as an option. Something like "Keep thumbnails of open windows" and "Keep thumbnails of all windows (breaks minimization)".

---

### Post by SmSpillaz on 2010-04-23
> **Zorael said:**
> It's left as an option. Something like "Keep thumbnails of open windows" and "Keep thumbnails of all windows (breaks minimization)".

It's gone in KDE 4.5 iirc

---

### Post by SmSpillaz on 2010-04-23
> **keljaden said:**
> Kwin has wobbly windows (which wobble nicer)
I like how the cube is done for when I am using my Desktop machine, but when using the laptop, I miss the ctrl+alt+rightarror to switch cube, but as I recall, that is being fixed in the next release of kubuntu (and hopefully kept with Linux mint 9 KDE as their 64 bit custom flash support is the best in linux).



Install ccsm and change the keybinding back.


> 

I have also noticed that Compiz has REDUCED the amount of effects in the past year.  I used to be able to have an aquarium inside my cube...for reasons I cannot fathom, they removed it.



I actually ported it to 0.9.0 - and it's still in 0.8 - you need to install it from git or install compiz-fusion-plugins-unsupported

> 

also, if I have wobbly windows on in Kwin, can I assume I have Kwin+composition?



yes.

> 

How did he get the windows to all float around in the backround and what did he use for screen capture. I have not seen ANY of these effects available in compiz-fuzion last release...[http://www.youtube.com/watch?v=Y4wB3GUemVw&feature=related](http://www.youtube.com/watch?v=Y4wB3GUemVw&feature=related)

IMO, I think beryl by itself was ten times better than compiz is right now...example
[http://www.youtube.com/watch?v=kYgV2GlsufI&feature=related](http://www.youtube.com/watch?v=kYgV2GlsufI&feature=related)
Look how epic that is!!! I want that!

Also anyone see [http://www.sun.com/software/looking_glass/](http://www.sun.com/software/looking_glass/) before?  Its a 3D DE from what I can tell...I like sun so much, first virtualbox, now this. kudos to those devs.

And thanks everyone for you replies so far!

Floating windows: '3D Windows plugin'
Beryl: Is discontinued and compiz has all of it's features?
Looking Glass 3D: Try the freewins plugin?

---

### Post by SmSpillaz on 2010-04-23
> **krazyd said:**
> Nope, kwin has this.
edit: I may have misunderstood 3Miro's statement. What I mean is that kwin caches the window state at the time of minimisation to provide previews. It doesn't continue rendering to a minimised window's pixmap.



Oh ok. Last I checked they didn't but maybe they have added it back as this instead.

I believe Beryl used to do that as well but it was also removed since it was sllllooooowwwww

> 
I'm intrigued.. what are these features?

Windows overlapping two or more desktops (since they use desktops rather than viewports)

---

### Post by keljaden on 2010-04-24
Will synaptic have the unsupported plug-ins, or must I get them from the compiz main site?

---

### Post by MountainX on 2010-07-02
> **keljaden said:**
> 

How did he get the windows to all float around in the backround and what did he use for screen capture. I have not seen ANY of these effects available in compiz-fuzion last release...[http://www.youtube.com/watch?v=Y4wB3GUemVw&feature=related](http://www.youtube.com/watch?v=Y4wB3GUemVw&feature=related)


RE: "windows to all float around in the backround"
Do you mean the task switching effects?

> **keljaden said:**
> 

IMO, I think beryl by itself was ten times better than compiz is right now...example
[http://www.youtube.com/watch?v=kYgV2GlsufI&feature=related](http://www.youtube.com/watch?v=kYgV2GlsufI&feature=related)
Look how epic that is!!! I want that!

Wow! That is impressive! And it is from 2006. Incredible.

---

