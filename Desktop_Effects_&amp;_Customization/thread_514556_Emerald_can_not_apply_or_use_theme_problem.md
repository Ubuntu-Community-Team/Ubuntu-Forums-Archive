---
title: "Emerald can not apply or use theme problem"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by yogo on 2007-07-31
I have Emerald installed and have downloaded and installed a couple of new theme, however there is not a wasy to select and use theme within Emerald.

I highlight the theme I want to use BUT THERE ARE not any options to apply or use current theme.

The only choice is to quit Emerald....?

What gives? Where do I apply the theme I want to use?


TIA

---

### Post by Malh on 2007-08-01
I'm pretty sure you have to type "emerald --replace" in a terminal.

---

### Post by FuturePilot on 2007-08-01
Are you using XGL? The theme should apply when you click on it.

---

### Post by acelin on 2007-08-01
I have the same problem! It does nothing.

Emerald replace does not work either.

What is up with XGL?

---

### Post by acelin on 2007-08-01
It comes up with this error when I type it in the terminal:


(emerald:6316): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

---

### Post by yogo on 2007-08-01
> **Malh said:**
> I'm pretty sure you have to type "emerald --replace" in a terminal.


Well I have a theme I really like that is not in Emerald and it works but I still am buffaloed as to why Emerald does not work.

Emerald is not displaying any theme, the themes are being displayed by the default Compiz that is installed in Feisty.

I tried running that command ( emerald --replace) , am I suppose to put the name of the theme to use after replace?

Like I said Emerald is not displaying any theme currently so I am not sure if the replace command would work....btw, terminal did find the theme that I am running and said it was not in Emerald WHICH IS TRUE.  That theme is in the ?compiz default that comes with Feisty.

Thanks

---

### Post by atomkarinca on 2007-08-01
are you sure emerald is your window-decorator? i don't what you use but you can check it from the icon on the system tray (i'm assuming you're using either beryl or compiz-fusion). after you make emerald your default window-decorator, those changes will take effect.

---

### Post by yogo on 2007-08-01
> **atomkarinca said:**
> are you sure emerald is your window-decorator? i don't what you use but you can check it from the icon on the system tray (i'm assuming you're using either beryl or compiz-fusion). after you make emerald your default window-decorator, those changes will take effect.



You are probably right there!

I have no icon for Emerald in sys tray so I am not sure as to what to enable to make it my Windows decorator???

TIA


PS I am using Beryl

---

### Post by yogo on 2007-08-01
Ok I got it all figured out, I did not have the Beryl manager installed.

Thus I had no ico, there were so many Beryl packages and I thought I had selected enoufh.

The second I installed the manager, viola Emerald now works!
\

Thanks for the icon tip atomkarinca, you got me on the right path to figure it out.

Resolved

---

### Post by subru77 on 2007-08-01
I am having the same problem too. Themes does not change when I select them in emerald. 

I have compiz fusion and emerald installed. 

Does this mean that I have to instll Beryl Manager as well? Will it clash with existing compiz installation? 

I am not a linux geek and I appreciate your detailed reply. Its grea tthat you are keeping this forum live and kicking.

---

### Post by xhizors on 2007-08-01
nah it's fine you can install both.

---

### Post by speedothebrief on 2007-12-08
> **acelin said:**
> It comes up with this error when I type it in the terminal:


(emerald:6316): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

I have the same problem!

```
emerald --replace

(emerald:8133): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

```

how to fix???!?!?

---

### Post by Bunnykun on 2007-12-15
I have the same issue!  started after a fresh install, and a second reinstall has not resolved the issue.  Assistance please!

---

### Post by jeyaganesh on 2008-01-03
I too have same problem. If i click some emerald theme and quit, nothing changing.  Each time I have to do 'Alt+F2' and then to type 'emerald --replace' to get emerald theme into the effect. I read some where 'compiz fusion' must work with emeral themes. They fused old compiz and beryl and created this new window manager 'compiz fusion'. 

Anyone out there to help us in choosing emeral theme?

Thanks in advance.
Jay

---

### Post by 5735guy on 2008-01-04
Sometimes this can happen if you are trying to run a Beryl emerald theme on Compiz.

---

### Post by jeyaganesh on 2008-01-10
Hi I just tried with compiz emerald themes on compiz fusion, still the themes are not changing until Alt+F2-emerald --replace.

---

