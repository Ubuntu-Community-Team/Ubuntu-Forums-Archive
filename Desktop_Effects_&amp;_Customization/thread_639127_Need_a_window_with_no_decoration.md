---
title: "Need a window with no decoration"
date: 2007-12-12
forum: Desktop Effects &amp; Customization
---

### Post by MrBiggz on 2007-12-12
Greetings!

How do you tell compiz to NOT decorate a window?  I'm trying to start Xion through wine and I think that compiz wants to throw a window around it when it really needs none.

Is this do-able?: roll:

Thanks in advance!

---

### Post by dpar on 2007-12-13
Why not just turn compiz off for the time being??> metacity --replace

---

### Post by bwakkie on 2007-12-13
Go to your compizConfig Settings Manager > Window decoration and add the title of your Decorate Window field like:

!title=^embedded$

it is saying: -- Decorate windows except when the title is precisely "embedded" --

this way compiz skips every window with the title embedded.

(ps. enable regex in your compiz settings)

---

