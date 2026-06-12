---
title: "Desktop effects only for the first user"
date: 2007-11-24
forum: Desktop Effects &amp; Customization
---

### Post by ulisesrangel on 2007-11-24
i have just installed ubuntu 7.1, dont haved splash screen but find the way to fix it in the forums, but could not find how to solve that, so im asking for any help.

basically, the first user that log in have desktop effects, but when switch user, the second only get plain old 7.04 desktop without effects.

laptop centrino gateway 505, intel 1.5, 512ram, ati 9600 pro (maybe without use, since after installing the restricted ati drivers, desktop effects stop working, i remove the driver and worked again, so i guess im using the intel integrated video card (if any), but i really dont know (how to know what card desktop effects use? or can do without card? software rendered?))

---

### Post by Forlong on 2007-11-24
That's normal. You can't have multiple users running and all of them using the effects.
I don't know if there's a graphics card that would be capable of doing this but more importantly you would have to use independent X-servers - which the switch users function in GNOME doesn't.

---

### Post by ulisesrangel on 2007-11-26
thank you for clear my mind...

just one more question, you mention something about x-servers (i really dont know that much) and that gnome dont support it in switch users...

do you know if it is posible in kde (or the other one that come in Kubuntu) and if kubuntu has desktop effects?

---

