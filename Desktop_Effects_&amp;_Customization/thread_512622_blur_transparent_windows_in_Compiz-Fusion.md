---
title: "blur transparent windows in Compiz-Fusion"
date: 2007-07-29
forum: Desktop Effects &amp; Customization
---

### Post by technikalKP on 2007-07-29
I have Compiz-Fusion running with Emerald.  Under Beryl, I was able to set it up so that semi-transparent windows blurred the images behind them to make readability better.  I can't seem to get this to work in Compiz-Fusion.  I have the 'Blur' plug-in enabled but it doesn't seem to work as you can see in the attached screenshot.

Any ideas on what I need to do to get this to work?

Thanks!

---

### Post by pointone on 2007-07-30
Add the word "any" in the "Alpha blur windows" text box.

---

### Post by psyopper on 2007-07-30
Good tip, thanks!

---

### Post by technikalKP on 2007-07-30
Tried that and still can't get it to work.  It works perfectly under Beryl, though.  I think I'll switch back for the time being and try compiz-fuzion again in a bit.

Thanks for your help!

---

### Post by dirn on 2007-08-12
After enabled blur windows in **CompizConfig Settings Manager**, open **Emerald Theme Manager** and go to **Emerald Settings** tab. There's a combobox for **Compiz Decoration Blur Type** choose either **Titlebar only** or **All decoration**.

Note : Please don't put **any** in the **Alpha blur windows** textbox unless if you have a lot of ram and a good graphic card or else it'll slow down your machine.

---

### Post by malachias on 2007-08-29
a nice alternative to 'any' is 'normal'... that seems to work for me. Although if someone knew how to make it work with only the gnome-terminal (beryl had a wonderful little 'grab' function where you'd click what you wanted to blur, but i forgot what the output was) I'd like that =)

---

### Post by Phristen on 2007-11-04
Sorry for bumping an old topic, but I seem to be having the same problem.

The suggestions given above:> After enabled blur windows in CompizConfig Settings Manager, open Emerald Theme Manager and go to Emerald Settings tab. There's a combobox for Compiz Decoration Blur Type choose either Titlebar only or All decoration.
> Add the word "any" in the "Alpha blur windows" text box.do not enable any blurring, but they do hang my machine as soon as I start moving windows around.

I have radeon x550, 1 Gb of ram and athlon64 3000+, and everything else runs smooth... What might the problem be?

P.S. By the way, what is the motion blur plugin supposed to do? It doesn't really do anything when I enable it.

---

### Post by megarek on 2007-12-02
Okay, I'm reviving this thread because I have an answer for you.  In the Blur windows settings, copy this into box "Alpha Blur Windows": "toolbar | menu | utility | normal | dialog | modaldialog"
That should make it work how you want.  See screenshot
Ross
PS First post

---

### Post by diwas on 2008-01-06
This is not working. I have 64MB Graphics card, 512MB RAM, 1.8GHz processor. The transparency is working fine, why is blur not working? Please help.

---

### Post by poo_22 on 2008-01-19
> **diwas said:**
> This is not working. I have 64MB Graphics card, 512MB RAM, 1.8GHz processor. The transparency is working fine, why is blur not working? Please help.
same:-(
! someone  help..

---

### Post by diwas on 2008-01-20
poo_22 it wont work in our system. The graphics used in blur is very intense and not at all supported by the 64MB internal. So no blur effect!

---

### Post by poo_22 on 2008-01-20
ok. thx for the info diwas.

---

### Post by diwas on 2008-01-21
You're always welcome. But it is sad that the blur wont work in our system. But lately i found cube plugin damn kool...hehe so no more BLURRRR hehe

---

### Post by dirn on 2008-02-04
> **malachias said:**
> a nice alternative to 'any' is 'normal'... that seems to work for me. Although if someone knew how to make it work with only the gnome-terminal (beryl had a wonderful little 'grab' function where you'd click what you wanted to blur, but i forgot what the output was) I'd like that =)

alternative to 'any' and 'normal' is 'class=Gnome-terminal'

[http://www.gnome-look.org/content/show.php/Hybrid+08.01?content=73252](http://www.gnome-look.org/content/show.php/Hybrid+08.01?content=73252)

blur effect will work fine if you have a good graphic card. I'm using Geforce 7600GS so it's okay on my machine to some level (Anti Alias will slow down the machine). Unfortunately, I can't do the same to my wife's machine as she's only used Geforce FX 5500.

---

