---
title: "Is siimply installing Compiz going to tax my cpu?"
date: 2010-07-02
forum: Desktop Environments
---

### Post by finny388 on 2010-07-02
I'm using an eeepc netbook. not powerful by any means.

but I was hoping to try Compiz to see if some features would not be too taxing.

Can I use Compiz a la carte and select specifically what features I do or don't want?

Is it possible to disable Compiz completely?

Do I want to install Compiz Fusion as well?

thanks!

---

### Post by VeeDubb on 2010-07-02
> **finny388 said:**
> I'm using an eeepc netbook. not powerful by any means.

**[COLOR="Red"]Well, some of them are.  The 1201n is dual-core, 64bit, and supports up to 4GB of ram; not to mention nvidia graphics.[/COLOR]**

but I was hoping to try Compiz to see if some features would not be too taxing.

**[COLOR="Red"]Go for it.[/COLOR]**

Can I use Compiz a la carte and select specifically what features I do or don't want?

**[COLOR="Red"]Yup.  Just be sure you install CCSM.  "Compiz Config Settings Manager."  That's where you'll go to turn pieces on and off.[/COLOR]**

Is it possible to disable Compiz completely?
[B][COLOR="Red"]
Sure.  You can turn all the functional bits off one by one through CCSM, disable all of it at once through the appearance settings program, or just remove compiz if it doesn't work out for you.[/COLOR][/B]

Do I want to install Compiz Fusion as well?

**[COLOR="Red"]Compiz Fusion IS compiz.  Once upon a time, compiz, beryl and maybe one or two other projects were out there to do the exact same thing.  The got "fused" together into compiz fusion.  Any time you've seen or heard a refference to "compiz" in the last couple of years, they meant compiz fusion.[/COLOR]**

thanks!


I think that pretty well covers it.

Oh, and it's also worth pointing out that compiz won't tax your CPU at all if you have a GPU that can handle the acceleration.  In fact, it has been argued that compiz can actually REDUCE the demand on your CPU by offloading many desktop rendering tasks to the GPU.

---

### Post by finny388 on 2010-07-02
Thank you very much.

In Synaptic there is:
OpenGL window and compositing manager (compiz)
Compiz (OpenGL window and compositing manager - GNOME window decorator)
Compiz Fusion Icon (Start and manage Compiz Fusion)

and I see CCSM as well

I'll install CCSM

but which of the first three do I choose?

---

### Post by VeeDubb on 2010-07-03
"Compiz,"  The one with the Ubuntu logo next to it.  That means it's a "supported" package.

Compiz Icon is just a quick launch button to turn it on and off, and not at all worth installing.

The other one is probably an alternate version of compiz from some non-standard repo.

---

### Post by finny388 on 2010-07-03
Thank you VeeDubb, it is prompt, friendly, informative replies like this that make me feel so great about Ubuntu and its community.

now on to try compiz :D

---

### Post by steveneddy on 2010-07-03
Another item you may want to install is called **fusion-icon**

After you install all of your Compiz stuff simply in terminal

```
sudo apt-get install fusion-icon
```

You will want to add this to the start up menu by merely adding the command

**fusion-icon **

in the appropriate place.

It usually sits in the upper bar next to the Network Manager. Just right click to select Compiz or Metacity and many other options.

---

