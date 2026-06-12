---
title: "Ubuntu/Pango bug back"
date: 2006-06-04
forum: Desktop Environments
---

### Post by jamyskis on 2006-06-04
I've just posted this same query on the Anjuta project forum with a hope that a solution might present itself.

I've use Anjuta for my C++ projects. It used to work fine until I installed Breezy, when a horrible bug with libpango/Anjuta came up, but to solve this I just installed a newer version of Anjuta. However, with the release of Dapper, there is no newer version of Anjuta (1.2.4a is the newest), and trying to upgrade/downgrade the version of Pango (1.12.2 is the Dapper standard, 1.12.3 is the newest) will most likely only break the system.

The bug isn't as bad as before, but there are number of character combinations that it doesn't like; st and ff for instance, which you can see in the screenshot - the function reset_enemies_tate(), which should and does say reset_enemies_state(). I've also put in a few f's to demonstrate the problem there. 

You'll notice that I'm running this in an Xgl server but it does the same thing in a normal X server.

Thanks for any light that anyone might be able to shed on this!

---

### Post by jamyskis on 2006-06-06
Anyone?

---

