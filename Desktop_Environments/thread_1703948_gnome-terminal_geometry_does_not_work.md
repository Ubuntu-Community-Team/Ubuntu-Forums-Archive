---
title: "gnome-terminal geometry does not work?"
date: 2011-03-09
forum: Desktop Environments
---

### Post by Kleenux on 2011-03-09
I did a search. But I'm not sure about the latest status - posts reporting a problem are pretty old.

So, is there a problem with gnome-terminal --geometry?

For instance 
```
gnome-terminal --geometry=100x50
```works fine.
but
```
gnome-terminal --geometry=100x50-0+0
```does not work.

The '-0+0' is either ignored or wrongly processed.
It should put the window sticked to the right side, and to the top.
But, instead, the window appears to be positioned randomly on the screen (while the size is correct, 100x50). :confused:

---

### Post by hictio on 2011-03-10
It works A Ok for me...
Try this:

```

gnome-terminal --geometry 100x50-0+0

```

Also, do you have Desktop Effects enabled? Perhaps one of the widgets is forcing an intelligent window placement?

---

### Post by Krytarik on 2011-03-10
I tried it with your commands and it works as expected.

If you are using Compiz, you could also use its "Place Windows" plugin for that:
"System -> Preferences -> CompizConfig Settings Manager -> Window Management -> Place Windows".

Of course this would mean that the terminal is always opened at the specified position.

---

### Post by Kleenux on 2011-03-10
Thanks for your answers.

I see that compiz is installed - by default since I didn't force it myself (Ubuntu 10.10).

The Visual Effects are set to Normal.

Are you on 10.10 maverick?

---

### Post by hictio on 2011-03-10
> **Kleenux said:**
> Thanks for your answers.

I see that compiz is installed - by default since I didn't force it myself (Ubuntu 10.10).

The Visual Effects are set to Normal.

Are you on 10.10 maverick?

Not me, plain vanilla Lucid Lynx 32 bits.

---

### Post by Krytarik on 2011-03-10
> **Kleenux said:**
> 
The Visual Effects are set to Normal.

Are you on 10.10 maverick?
Me neither, see left.

Then just put it the Compiz way.

---

### Post by Kleenux on 2011-03-10
It works on my other Ubuntu 10.04.1...

So I'm guessing there is a bug in gnome-terminal from 10.10.

I'm looking at a simple, works anywhere solution, so compiz is not an option.
```
gnome-terminal --geometry=100x50-0+0
```should just work...

This is probably a bug.

---

### Post by cipherboy_loc on 2011-03-10
Running the command gets a window of the correct size, but at the right part of the screen for me. Currently, I am running Ubuntu 10.10 + Fluxbox (which might be my issue). If I log back into gnome sometime today, I will let you know if it works any better.


Cipherboy

---

### Post by mcduck on 2011-03-11
> **Kleenux said:**
> Thanks for your answers.

I see that compiz is installed - by default since I didn't force it myself (Ubuntu 10.10).

The Visual Effects are set to Normal.

Are you on 10.10 maverick?

Then you *are* using Compiz. :)

Just install CompizConfig Settings Manager and you can configure the geometry options there. The settings you need are in the "Place Windows"-plugin's options, under the "Fixed Window Placement"-tab.

(Visual Effects set to "None" uses Metacity as window manager, "Normal" and "Extra" both use Compiz)

---

