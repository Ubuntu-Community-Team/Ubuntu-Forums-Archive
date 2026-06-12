---
title: "kubuntu &amp; composite, transparency"
date: 2005-06-14
forum: Desktop Environments
---

### Post by arendald on 2005-06-14
I read here and there it is possible to use composite and transparency on kde. I know it is.

I'd like to know if there are some minimal hardware requirements to do so on kubuntu Hoary (xorg 6.8.2, kde 3.4.0) : ram, processor, graphic card (which is, I guess, the most important point).
When I say 'minimal requirements' I mean hardware requirements to actually still have a workable desktop and not a buggy turtle which looks good on a static screenshot and feels like shit when using it lol

And if you are using it what are your settings (xorg.conf modifications, settings in kcontrol center/desktop/window behavior/translucency).

Thanks

P.S. I use kubuntu with a 2.6.10-5-686-smp kernel (bi Athlon MP 1900), 768 Mb and a Leadtek based on GeForce Ti 4200 128 Mb. Edit : my desktop is 1280x1024x24 bits @ 85Hz on a 19" monitor with nvidia drivers.

---

### Post by felipe on 2005-06-14
i guess you should be ok, my system:
amd sempron 2800+
1 GB Ram
GeForce FX 5500

it runs very smooth and quite stable (never crashes, just some glitches here and there). as for the suggested settings... see this wiki entry

[http://www.ubuntulinux.org/wiki/DropShadows](http://www.ubuntulinux.org/wiki/DropShadows)

---

### Post by arendald on 2005-06-14
Do you use Gnome or Kde ?

Kde has built-in support for transparency, do I need to install the xcompmgr utility ?

---

### Post by Freddy on 2005-06-14
Yes you need to install xcompmgr first and do all the changes in your x.org conf file, If you use transparacy, Remeber that transparacy does't work that well with other opengl stuff in the background, so don't use a screensaver from the opengl section, and some of the graphics in amaroK player window, can make your kde crash.

/Freddan

---

### Post by shakin on 2005-06-14
[QUOTE=Freddy]Yes you need to install xcompmgr first and do all the changes in your x.org conf file, If you use transparacy, Remeber that transparacy does't work that well with other opengl stuff in the background, so don't use a screensaver from the opengl section, and some of the graphics in amaroK player window, can make your kde crash.

/Freddan[/QUOTE]

Are you sure KDE needs xcompmgr? I used that with Gnome, but I don't think KDE uses the same  composite manager because xcompmgr worked ok for me in Gnome, but KDE's composite manager is very buggy on my i915 video card (all windows turn into black shadows).

---

### Post by arendald on 2005-06-14
Still not sure I have to install xcompmgr. I use kde 3.4.0 and it is supposed to support transparency and composite stuff : Control center, Desktop, Window Behavior, Translucency.

---

### Post by rosslaird on 2005-06-14
As I recall, the transparency/translucency that KDE supports is not authentic transparency: it makes a copy of what's behind a translucent object and shows it in the foreground of the object (faded or otherwise), whereas xcompmgr uses actual transparency. The next version of kde will use actual transparency from the X server (xcompmgr and the composite extension). At the moment, the only authentic transparency in KDE  must be done by using xcompmgr and transset manually.

I could be wrong...

---

### Post by Freddy on 2005-06-14
Yep rosslaird, you recall totally right. 
You can for example make your console transparent, but it only takes a snapshot from your wallpaper and uses that as a background, the same for a transparent kicker, 

xcompmgr with the composite extension in x.org conf file allows real transparacy (where you actually see whats behind) but thats it's quite buggy and doesn't work well with other opengl applets.

/Freddan

Edit: you don't need to use transet though, you can set it how to use those type of effects (trans, shadows, fade in/out) in controlcenter|desktop|windowbehavior|translucency or just choose how much trans to use for the specific window in windowmenue|opacity

This is if you already installed xcompmgr and made the necessary conf file changes.

Edit again: If you choose not to install xcompmgr and add the necessay lines to x.orgs conf file you and then try to enable transparacy, you will be greeted with a error for that effect upon entering kde, at least that what it did for me, had to test it :)

---

### Post by GameManK on 2005-06-14
those edits to the xorg config file for hardware acceleration, are they only useful for transparency, or can other KDE eye candy be improved that way? for example, panel hiding animation

if so, is it safe?

---

