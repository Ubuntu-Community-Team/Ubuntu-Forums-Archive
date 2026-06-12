---
title: "Xgl / Compiz Help"
date: 2006-08-24
forum: Desktop Environments
---

### Post by Hyakutaro on 2006-08-24
I recently installed Xgl w/ Compiz and it's really wonderful. However there a couple of things that are bugging me.

1) I seem to have no control over Xgl, it's like the keyboard shortcuts do not to work, only Alt works when a window is active... it moves it to another workspace. I cannot control the cube or do anything... 

2) The water effect does not seem to work, although the plugin is checked **Gset-compiz**... can someone tell me what's wrong?

Thanks for everything :)

---

### Post by asplode on 2006-08-24
Hey at least you got it to work at all for you, I've tried several times on several installations, and all it does it eat my gnome toolbars and all my window chrome.

---

### Post by mjreged on 2006-08-24
You are going to have to stick to what works.
Using quinn's repos or the vanilla repos from compiz.net 
will give you challange since they have cicles or turbulence as they add, change, modify packages. In the things break.
Like the Gset-compiz lately does not work properly with the keys setup etc,,

For example,
some guides become absolete due to package naming, hence

when i tried to install  compiz-vanilla-aiglx 
dependency broke due to missing gset-compiz.

however, a new compiz-gnome-manager contained what i needed from compiz-vanilla-aiglx.
hence you have to be aware of those kind of changes

---

### Post by Hyakutaro on 2006-08-24
Oh I see... so we'll basically have to wait? 
I tried Xgl with **Kororaa** and it worked perfectly... 

Xgl / Compiz installed without any problems on Ubuntu... I would really like to fully enjoy its feature though :(

---

### Post by ayoli on 2006-08-24
ctrl+alt+arrow (left or right) move the cube, or with ctrl+alt+left clic and moving the mouse. water effect do not work for me (and for some people here).
a gset-compiz package can be found [here]("http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/") and apt-get install -f should fix some install/upgrade problems.
regards.

---

### Post by Pantuflo on 2006-08-24
You can follow this link to enable the super-key:
[http://linuxman.blogsome.com/2006/08/11/como-establecer-la-tecla-super-key-en-ubuntu/](http://linuxman.blogsome.com/2006/08/11/como-establecer-la-tecla-super-key-en-ubuntu/)
(in Spanish, I think it's easy to understand).

Enabling it, I have managed to use the "Alt+Tab" for 'switcher', the "Super+Scroll" for zooming, moving the cube well...

However, I can't do the water effect yet. "Ctrl+Super" key places the active window on the left of the screen (?). I've also checked that the "Alt" key sends the active window to another workspace.

I have also checked that I have the plugins in the correct order, in the conf dialog (from top to bottom: gconf, decoration, transset, wobbly, fade, minimize, cube, rotate, zoom, scale, move, resize, place, switcher, trailfocus, water -- although there are some other plugins).

---

### Post by Hyakutaro on 2006-08-25
Thanks, I'll try these later. Anyway are these Ubuntu-only related problems?
Or its the same case with other distros?

---

### Post by distroman on 2006-08-25
I think ubuntu, would actually be the best supported.
If you just setup xgl/compiz, then your keyboard layout might be wrong.

---

### Post by ayoli on 2006-08-25
maybe you can try:
```
xmodmap /usr/share/xmodmap/xmodmap.fr
```
replace xmodmap.fr with one corresponding to your language.
regards.

---

### Post by Hyakutaro on 2006-08-25
@**distroman**: I don't think there's something with my keyboard, it worked fine with other distros that had Xgl w/ Compiz. And it worked fine with everything in Ubuntu... 

@**ayoli**: I'll give it a shot, thanks :)
[B][U]
EDIT:
[/U][/B]

Okay I have tried that with .us_intl at the end.. no errors or anything.. jsut nothing happens :P

Any ideas guys? I really want to control the cube :P

---

### Post by ayoli on 2006-08-25
the shortcuts that move the cube for me seems to be here (in gconf-editor):
```
/apps/compiz/plugins/rotate/allscreens/options/rotate_left_key
/apps/compiz/plugins/rotate/allscreens/options/rotate_right_key

```
hope it could help,
regards.

---

### Post by Pantuflo on 2006-08-25
I have to say that I have a strange behaviour with shortcuts:

Xgl/Compiz works well, I can say wobblig effect when I move windows. Plugins are enabled in the conf, and it's a recent installation.

I have enabled this command on startup:
```
xmodmap /usr/share/xmodmap/xmodmap.es
```
I'm spanish and I think this is the right code I should be using.
Also I'm using the compiz-start.py on startup.

But when my session starts, I can't use any shortcut (Ctrl+Alt doesn't work, I can't rotate the cube with the mouse at the edge of the screen...). Then, I enable the super-key in "Preferences-keyboard", and it seems that "something happens :confused: " and shortcuts become usable (Ctrl+Alt, mouse zooming...), although some keys seems to do some things at the same time; e.g. I want to press "alt+TAB" for make "switcher" to work, and at first, "Alt" key sends the active window to another face of the cube, and then "Alt+TAB" shows the "switcher" as it should do...

It also seems that the xmodmap command resets the "super-key" config, so I have to enable it every time I login.

I will investigate more about this, maybe it's concerned with a wrong keyboard configuration.

---

### Post by Hyakutaro on 2006-08-25
It worked! It worked! I can control everything!

Ok, *calms down* ... I opened the gconf editor and went to 
```

/apps/compiz/plugins/rotate/allscreens/options/rotate_left_key
/apps/compiz/plugins/rotate/allscreens/options/rotate_right_key

```

I enabled what was disabled... works fine now :)

---

### Post by Pantuflo on 2006-08-25
> **Hyakutaro said:**
> I enabled what was disabled... :)

What have you exactly enabled? So does the water effect work for you too?

I managed to solve my situation changing the keyboard layout, I haven't changed anything special in gconf-editor. However, water doesn't work.

---

### Post by Hyakutaro on 2006-08-26
Actually I was wrong in my previous post, changing the keyboard layout DID solve my problem...

---

