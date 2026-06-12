---
title: "Easy way to enable/disable Compiz Fusion (KDE)"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by rainefan on 2007-06-26
Hi people!

I'm using Compiz Fusion installed based on this tutorial ([http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion&page=13](http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion&page=13)).

But, since i'm using my work's PC, and also, it's config it's not good enough to use Compiz + Firefox + Eclipse + etc :D. I was trying to find a way to switch back (without uninstalling compiz and friends) to my  KDE native window_decorator disabling compiz.

I tryied 'killing' compiz processes but window decorator disapears and then the only way is to restart X server (CTRL+ALT+BACKSPACE), but compiz processes emerge again :(

So, could you guys help me finding a way to enable/disable easily Compiz Fusion for KDE?

Tnx!

Regards,
Raine

---

### Post by rainefan on 2007-06-26
Boing!

Please help!

---

### Post by FluffyBunny on 2007-06-26
You can switch between them using two simple commands. This is how I switch between them for running accelerated games, and at work because I have the same problem.

Use alt-F2 to run a command 
 
compiz --replace    # to turn compiz on

kwin --replace  # to revert to kwin

FluffyBunny

---

### Post by Plaaa on 2007-06-27
what is kwin ?
don't work for me...

---

### Post by bigken on 2007-06-27
works ok for me ;)

---

### Post by rainefan on 2007-06-27
:o Thanks FluffyBunny! It just worked as i expected!
Just sumarizing:

To start compiz+emerald from kde:
```

compiz --replace -c emerald &
killall kwin #just for the case it has some kwin processes

```

To swich back to 'normal' mode in kde:
```

kwin --replace &
killall compiz compiz.real # mandatory!

```

Best regards and thanks!,
Raine

---

### Post by jamesrl on 2007-07-16
To do the same thing in gnome running the default window manager (metacity) you can do the same thing for enabling as above.

To enable (using compiz fusion with metacity as window decorations):
```

compiz --replace

```

or to use compiz fusion with emerald as window decorations (which is more configurable and allows a few more things for compiz to do)
```

compiz --replace -c emerald &
killall metacity #just for the case it has some kwin processes

```

To disable compiz and restart metacity (for me this makes watching videos easier; don't have to use gstreamer-properties to set unaccelerated X11; can use XV):
```

metacity --replace &
killall compiz compiz.real
```

Note: I am not sure if the compiz.real  is necessary in the killall, as it didn't seem to kill anything when I ran it; however it can't hurt.

---

### Post by mpstump on 2007-11-17
Help! I tried installing compiz using this thread, and now my systems hangs for about 2 minutes after the log in screen, then comes back to the login screen. How do I restore the damage? I'm assuming some display manager is working, because when xorg failed, I wouldn't even get a login screen.

Thanks!

---

### Post by rphil2008 on 2008-06-15
> **FluffyBunny said:**
> You can switch between them using two simple commands. This is how I switch between them for running accelerated games, and at work because I have the same problem.

Use alt-F2 to run a command 
 
compiz --replace    # to turn compiz on

kwin --replace  # to revert to kwin

FluffyBunny

Thank you FluffyBunny! I am testing the Knoppix 5.3.1 Live DVD with compiz-fusion autostarting. Rather than individually turning off its configuration options, I tried your suggestion and they work, back and forth!

---

