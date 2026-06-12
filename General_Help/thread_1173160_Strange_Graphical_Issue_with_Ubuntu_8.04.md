---
title: "Strange Graphical Issue with Ubuntu 8.04"
date: 2009-05-29
forum: General Help
---

### Post by RocketDarkness on 2009-05-29
Heya everyone, I hope you can shed some light on this bizarre situation. I've got a machine that currently has Ubuntu 8.04 'Hardy' server installed on it. We wanted to try out a program that required a graphical interface, so I ran 'apt-get install ubuntu-desktop'. Which worked, but the graphical interface is a mess. Almost everything looks oversaturated with light, and icons are impossible to make out. It's un-navigable if you weren't already familiar with the desktop layout. 

One very odd thing I noticed is that when it prompts you to put in the superuser's password and it darkens the screen, it looks perfect. Is there any way to tweak the settings so it doesn't look weird as heck? 

One other thing I noticed is that using the screenshot function, and looking at the image on another working PC, is that the image looks fine. So clearly it THINKS it's outputting correctly.

The last thing, is that when I stuck Ubuntu 6.06 'Dapper' in the CD drive, the trial output looks perfectly fine. So I'm at a loss for exactly what's going on here. Advice would be appreciated. =)

---

### Post by pastalavista on 2009-05-29
I'm just guessing that since you're running the server distro, you probably don't have X configured right. Try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by YenTheFirst on 2009-05-29
hmm. Maybe the gamma settings are messed up?

In an Xterm, run "xgamma", it will output the current gamma settings.
"xgamma -gamma 0.1" should make your screen incredibly dark
"xgamma -gamma 1" should make your screen normal

Let me know if that's it, or not.

---

### Post by RocketDarkness on 2009-05-29
> **YenTheFirst said:**
> hmm. Maybe the gamma settings are messed up?

In an Xterm, run "xgamma", it will output the current gamma settings.
"xgamma -gamma 0.1" should make your screen incredibly dark
"xgamma -gamma 1" should make your screen normal

Let me know if that's it, or not.

If I drop it really low, to .3 or .4, the graphical stuff seems to be much more easily visible. I think it messes with the color of some other stuff (The default heron wallpaper is now dark red and black, for instance), but I can navigate again. It's a good enough fix for now, at least.

I tried the dpkg thing, but it didn't seem to fix anything unfortunately. Perhaps I told it the wrong thing in the graphics question? ::shrug::

---

### Post by YenTheFirst on 2009-06-02
> **RocketDarkness said:**
> If I drop it really low, to .3 or .4, the graphical stuff seems to be much more easily visible. I think it messes with the color of some other stuff (The default heron wallpaper is now dark red and black, for instance), but I can navigate again. It's a good enough fix for now, at least.

I tried the dpkg thing, but it didn't seem to fix anything unfortunately. Perhaps I told it the wrong thing in the graphics question? ::shrug::

hmm. I was under the impression before that everything had been 'over saturated with light'.

Was the wallpaper fine, and only desktop icons and menus were messed up?
Is it possible, perhaps, that a high-contrast theme got installed?

---

