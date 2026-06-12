---
title: "KDE4 Menu's"
date: 2008-01-11
forum: Desktop Environments
---

### Post by mrbones on 2008-01-11
Seem to have a stupid issue, I am fine for the time being not having all my icons. I however would like the ability it add my images for the icons if I want to. In KDE4 however (just put it on today), I cannot seem to get my menu editor up and running, the program doesn't seem to exist. and when you right click it just asks you some general questions.

I know KDE4 just came out as stable, but this is just a bit annoying.
Your help is appreciated.

---

### Post by phinn on 2008-01-12
I'm having the same issue,  most of my icons are just question marks.

Overall the KDE4 gui isn't that good, it seems like they couldn't decide on what to do for several things.

---

### Post by andrewsomething on 2008-01-12
I also can't seem to run the KDE4 menu editor.... Running KDE 4 from the PPA repo over Ubuntu 7.10. Hopefully they'll add the package and update the meta package that should pull it in when they do.

---

### Post by mrbones on 2008-01-12
Im hoping its fixed by 4.1 or even as some little .deb file with some sort of fix. 
Well glad to see its not just me, But yeah, it seems like they just wanted to rush KDE4 to make the deadline.
*edit*
Also wanted to add though, the bar itself isnt resizable, you cant (yet that I have seen) move where the icons get placed. 
But on the otherhand, I do love the idea for the shiny black look, and the widgets(if they would work too).

---

### Post by izi on 2008-01-13
try

```
kmenuedit
```

worked for me. It's not integrated into the right-click menu which is too bad. 

The new KDE4 is BEAUTIFUL and some things are great (like Dolphin) but overall I get the feeling they went a bit GNOME'ish in their concept - blocking a lot of customization from the users (why no extra panels, why cant I change the size/location of that HUGE black thing on the bottom of my desktop, and what's up with the desktop management ? )

Nevertheless, Its still by far the best alternative

---

### Post by mrbones on 2008-01-14
> **izi said:**
> try

```
kmenuedit
```

worked for me. It's not integrated into the right-click menu which is too bad. 

The new KDE4 is BEAUTIFUL and some things are great (like Dolphin) but overall I get the feeling they went a bit GNOME'ish in their concept - blocking a lot of customization from the users (why no extra panels, why cant I change the size/location of that HUGE black thing on the bottom of my desktop, and what's up with the desktop management ? )

Nevertheless, Its still by far the best alternative


Right on thanks for the idea, Im at work right now... once I get back homeI will be trying that.

---

### Post by GeneralZod on 2008-01-14
> **izi said:**
> try
The new KDE4 is BEAUTIFUL and some things are great (like Dolphin) but overall I get the feeling they went a bit GNOME'ish in their concept - blocking a lot of customization from the users (why no extra panels, why cant I change the size/location of that HUGE black thing on the bottom of my desktop, and what's up with the desktop management ? )


See here for the actual reasons that you can't do this yet:

[http://software-libre.rudd-o.com/KDE_4.0.0_emergency_FAQ#Why_can.27t_I_auto-hide.2F_resize_the_panel.3F__Can_I_add_a_new_panel.3F](http://software-libre.rudd-o.com/KDE_4.0.0_emergency_FAQ#Why_can.27t_I_auto-hide.2F_resize_the_panel.3F__Can_I_add_a_new_panel.3F)

---

### Post by epsilon72 on 2008-01-14
For me 'kmenuedit' brings up the editor, but it is editing 3.5.7's menu instead (which is concurrently installed with 4).

I'm using gentoo though, and am running the latest svn version of KDE rather than 4.0 (probably not that much different.)

---

### Post by andymushu on 2008-01-14
I am having the same issue in kde 4. kmenuedit works, but, as already stated, it brings up the menu for kde 3.5, instead of 4. This really needs a fix...

---

### Post by dagwud on 2008-01-15
> **mrbones said:**
> 
Also wanted to add though, the bar itself isnt resizable, you cant (yet that I have seen) move where the icons get placed.
Just figured out you can arrange the icons by being sneaky-sneaky - remove the taskbar, pager, system tray, new device notifier, etc (so you've only got the menu left) then add the widgets you want in the order you want them (left to right).

Hopefully the core issue will be addressed, but this should do for now.

PS: Anyone got any creative ideas as to how to add some sort of spacer? I'd ideally like some space between my panel (ie. 'QuickLaunch' type icons) and my taskbar, but my approach of adding a 'Generic Icon' and changing it's icon to something near-invisible turned out disasterous (I don't recommend trying this - things get nasty when you try to modify the apparently-non-existant Generic Icon file)

---

### Post by Nezing on 2008-01-17
Here's what might be a silly question.I installed the kde 4.0 desktop,and after a system-wide freeze,a reboot,a couple of crashes,everything seems ok now.I have added what icons I want to the "huge" black taskbar,and they all work fine.But instead of a shiny blue "K" button at the far left of the taskbar,I have a shiny blue arrow,pointing left!!! Very annoying.I only use 1 desktop,and not the available choice of 4-my decision,but that is what I want-so where on earth did the blue letter K go?
As a final note,I use Firefox to browse the web,as Konqbrowser kept crashing.I know kde 4.0 is buggy,and version 4.1 (should) work perfectly,so a few niggles are part of the experiance I suppose.

:confused:

---

### Post by GeneralZod on 2008-01-17
It's highly unlikely that 4.1 will "work perfectly", but it should be much improved.

If Konqueror crashes frequently, please install the -dbg packages for KDE4 and submit bug reports - bugs won't get fixed if they don't get reported!

---

### Post by Nezing on 2008-01-17
Hmnn.Might not be the** correct** way,but I have removed the "arrow" icon,from the taskbar,and on the desktop,I have put the Application Launcher icon.From here I can access all that I want.
What happened to "K" I have no idea,but that "useless" blue arrow is no more.

:guitar:

---

