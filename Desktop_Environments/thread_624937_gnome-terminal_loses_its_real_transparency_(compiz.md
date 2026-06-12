---
title: "gnome-terminal loses its real transparency (compiz)"
date: 2007-11-27
forum: Desktop Environments
---

### Post by Alex Dinamo on 2007-11-27
Hello. I have Gutsy, and among several problems I am still fighting to resolve, I have this minor one:

When I specify transparency for gnome-terminal, I get real alpha transparency, cause I am on compiz, etc. and everything is great. However, when I restart the next day, real transparency for gnome-terminal is lost and I just get the old fake transparency, which shows the background but not my icons, for instance.

And this happens with the gnome-terminal that was saved as part of the session. If I close that one and open a new one, the real transparency is back there.

How do you find this?

Thanks,
Alex

---

### Post by Alex Dinamo on 2007-11-28
Nobody? really? Am I the only one having this problem? Or is it just "not important"?

Alex

---

### Post by Angafirith on 2007-11-28
If you have a gnome-terminal open before Compiz, the terminal will have the fake transparency. Is this the case?

Either way, try opening another gnome-terminal window and see whether it has the real transparency or the fake transparency.

---

### Post by Alex Dinamo on 2007-11-29
Yes, I think the problem has to be in the order the session is brought back. I think that, somehow, the terminal is brought back BEFORE compiz is already there, and so the terminal, failing to find compiz, fakes transparency...

This gotta be a bug, right?

Alex

---

### Post by Stemp on 2008-02-19
> **Alex Dinamo said:**
> Yes, I think the problem has to be in the order the session is brought back. I think that, somehow, the terminal is brought back BEFORE compiz is already there, and so the terminal, failing to find compiz, fakes transparency...

This gotta be a bug, right?

Alex

Yes I guess it's a bug, but I don't know where to fill it :(
In Compiz, in gnome-terminal ? 

Even if it's not a big deal, it's boring.

---

### Post by imoatama on 2008-02-21
Not a bug. Compiz can hardly know how to treat the window if its not yet running.

Simple workaround is to change the startup command to "sleep 10 && gnome-terminal --window-with-profile=transparent" (or whatever you named the transparent profile)

---

