---
title: "Can you stop Compiz from darkening the screen when you zoom in REALLY close?"
date: 2008-03-01
forum: Desktop Effects &amp; Customization
---

### Post by PiggiePaul on 2008-03-01
I'm not quite sure why they have done this, and would like to stop it happening.

When you zoom in a lot, the screen gets darker and darker, to the point where, a few pixels fill the entire screen it's almost black.

Anyone know if you can stop this happening (or why it's even done in the 1st place?)

---

### Post by PiggiePaul on 2008-03-02
Ok, seeing as there's no replies, may I just check with others............

Assuming it's "Just the way it is"

Can others please confirm that they too see the screen darken as they zoom REALLY close into things?

On my machine it's by holding down the SUPER key (Start key) and using your mouse scroll wheel.

---

### Post by Anduu on 2008-03-02
I will confirm for you it gets darker.Why I don't know.How to disable it...beats the heck out of me.I thought it might have to do with the trailfocus effect but disabling it doesn't change anything.

I'm guessing thats just the way it is?

---

### Post by cookieofdoom on 2008-03-02
Turning off lighting under ccsm --> general --> display settings should do it. You might have to restart compiz for it to take effect (compiz --replace).

---

### Post by meho_r on 2008-03-02
Thanks, that did it. BTW, does anyone knows how to turn off darkening when a window/app is not responding? It could be pretty annoying

---

### Post by cookieofdoom on 2008-03-02
The "ping delay" slider under general controls how long before a window goes gray. You can set that so that it's pretty long, but as far as I can tell there's no way to turn it off.

---

### Post by PiggiePaul on 2008-03-03
> **cookieofdoom said:**
> Turning off lighting under ccsm --> general --> display settings should do it. You might have to restart compiz for it to take effect (compiz --replace).

Thanks from me also.

Yes, that does do it, unfortunately it also kills the lighting for the 3D cube (light source from a point in space) and makes the cube look very flat.

I'll leave as it is, as I don't often want to zoom in silly levels.

But good to know how to change it.

Perhaps they will one day give the ZOOM function an override lighting option.?

---

### Post by Anduu on 2008-03-03
Yeah that's a shame it doesn't have its own lighting configuration :(

---

### Post by meho_r on 2008-03-04
> **cookieofdoom said:**
> The "ping delay" slider under general controls how long before a window goes gray. You can set that so that it's pretty long, but as far as I can tell there's no way to turn it off.

Thanks, that makes life little easier:) I'm using a graphic app through wine and every time I hold mouse for a while it is interpreted as app has been hanging. Now with max ping delay (30000) I can hold mouse at least for a minute which is enough of time:) Thanks again

---

