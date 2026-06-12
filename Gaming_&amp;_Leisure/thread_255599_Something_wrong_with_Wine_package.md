---
title: "Something wrong with Wine package"
date: 2006-09-11
forum: Gaming &amp; Leisure
---

### Post by keithjr on 2006-09-11
Hello,
  I'm trying to get Steam up and running so I can play Half-Life and its mods in Ubuntu.  I got the latest wine package, 0.9.20, and followed the linux-gamers how-to for starting up Half-Life ([http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games))

  Everything goes smoothly until I actually try to start a game (CS 1.6 is the one I'm working with), at which point I get an error that is not mentioned in the How-to, one that states that the video mode isn't supported and that it will now run in Software render mode.

  I looked into it, and the [answers]("http://lhl.linuxgames.com/howto/half-life-HOWTO-0.5.html#AEN251") that I found relate to the driver libopengl32.so, and like [this poor soul]("http://www.linuxquestions.org/questions/showthread.php?t=377836"), I find that I do not actually have this driver ANYWHERE on my system.  To make matters worse, that post references putting things manually into the config file, which I assume should be in ~/.wine/config.  I do not have this file either.

What the heck is wrong with the ubuntu wine package?  It seems like numerous important files are just not there.

---

### Post by keithjr on 2006-09-11
oh and to answer the obvious questions... I'm using an ATI 9600, have working drivers:

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

and other OpenGl games, like UT2004, work fine.

---

### Post by IAmNotPhillip on 2006-09-11
Run winecfg in the terminal to fix the missing config issue.

Wine doesn't come with the config stuff. It it generated on-the-fly once you run this command.

EDIT: Actually, scratch that. My wine works fine (most of the time) but the config file isn't in .wine either. So I'm not sure where it is stored. :P

---

### Post by keithjr on 2006-09-11
yeah, I already ran winecfg, should have included that.

I solved my problem though, I just changed the Windows Version to Windows 2000 and now CS doesn't complain about graphical modes.  Odd.  I can't argue with success, though.

---

### Post by HAARP on 2006-09-11
There should be some "registry" files in ~/.wine. The configuration is usually saved in there, along with windoze and applications settings. They're editable with normal text editors, but it's a pain in the *** to find the actual keys and their syntax. You're better off using winecfg
btw. keith, check your Spring forums IM ;)

---

### Post by keithjr on 2006-09-12
winecfg doesn't have an entry for opengl32 in the DLL overrides.  

And my problem has resurfaced.  For some reason whenever I try to save a new application, it just disappears after I leave winecfg.  And the settings will randomly not work anymore, once again resulting in the "unsupported modes" error.

Once again wine fails me.

---

