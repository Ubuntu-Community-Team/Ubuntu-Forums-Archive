---
title: "Emerald Theme Manager Won't Switch Themes"
date: 2007-03-13
forum: Desktop Environments
---

### Post by tsantos on 2007-03-13
I have beryl up and running on Xgl with an ATI video card.  Somehow, I managed to pick a theme at one point but the Emerald Theme Manager won't let me switch themes.  I can look at the list of them but selecting them doesn't change my theme.

In order to get beryl working (no white screens), I have to launch beryl like this:

```
beryl-manager --no-force-window-manager
beryl-xgl --use-copy
```

Could that be the reason that the Emerald Theme Manger won't switch me to other themes?

Is there a config file somewhere where I can force the change?

Thanks,

-Tom-

---

### Post by Waappu on 2007-03-15
> **tsantos said:**
> I have beryl up and running on Xgl with an ATI video card.  Somehow, I managed to pick a theme at one point but the Emerald Theme Manager won't let me switch themes.  I can look at the list of them but selecting them doesn't change my theme.

In order to get beryl working (no white screens), I have to launch beryl like this:

```
beryl-manager --no-force-window-manager
beryl-xgl --use-copy
```

Could that be the reason that the Emerald Theme Manger won't switch me to other themes?

Is there a config file somewhere where I can force the change?

Thanks,

-Tom-

Hi

If you right click that red diamond in notification area, you are able to set those same options to defaults under Advanced Beryl Options.

Try install Emerald themes ```
sudo apt-get install emerald-themes
```or re-install```
sudo apt-get reinstall emerald-themes
```

---

### Post by 7Notes on 2007-03-16
Hi there,

Realise this is an old thread but thought I'd post my workaround incase anybody browses across it,,,

I have the same issue as tsantos - selecting a new theme in Emerald Manager doesn't change the desktop straight away. I'd installed Beryl previously and it would change straight away - but given this time around the system seems to be stable (ATI Mobility 9700 + fglrx + XGL desktop) I'm not too worried.

The workaround for me is just to click on the Beryl notification icon and then click "Reload Window Decorator", which pretty much does what it says on the tin with the new theme in place.

I'd be interested if anybody has found an actual *solution* though!

---

### Post by got_nix on 2007-03-26
i'm curious to know if it actually themees the bottons and icons with the beryl emeral dthemes.. cause.. i honestly dont get that on my notebook.. only the window decorator is replaced. the icons and folders still look the same.

---

### Post by s0cket on 2007-03-26
If I was to guess I'd say dbus is failing in some way.  That or beryl's abliity to use dbus correctly.

---

### Post by omrsafetyo on 2008-07-22
I realize this is an older thread, but its still the top google hit - so it should have relevant data.

This can often be fixed by running "emerald --replace" as a start-up job.
You can run this once in the terminal, and the switcher will work - but chances are you will have your gnome theme back at next boot-up.  You need to run this as a start-up command and it will process correctly.

---

