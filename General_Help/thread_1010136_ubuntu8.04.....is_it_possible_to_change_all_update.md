---
title: "ubuntu8.04.....is it possible to change all updates to intrepid?"
date: 2008-12-13
forum: General Help
---

### Post by Meow27 on 2008-12-13
the title is a little misleading but here goes:

there are a bunch of programs out there (newly updated ones) that require newer versions of gtk2 and other things (that have dependencies of their own which would need to be updated!)things like libpango and libcairo2 are too old for certain programs to be installed... is there some other way to update all of these dependencies without constantly having to tediously manually update every single package?

im sure this has been posted before, [my apologies] but i have no idea what to search for :/

(p.s. i downgraded from intrepid to hardy cause of compatibility issues with my hardware so switching back there isn't an option :P)

thanks in advance

---

### Post by hikaricore on 2008-12-13
There are ways to force these types of installs, but this will involve manually editing the dpkg status file and I really can't suggest that unless you know what you're doing.

The best idea would be to see your software is available through an alternate repo or on getdeb.net.

If that's not the case you're usually better off uninstalling the current version and compiling the latest version from source.

---

### Post by Meow27 on 2008-12-13
> **hikaricore said:**
> 
If that's not the case you're usually better off uninstalling the current version and compiling the latest version from source.

but it IS the case -_- Gimp for instance, needs a newer version of gtk and (the new) gtk needs libcairo2 which needs all of its other things etc.....

i dont care that much as to what im doing. as long as my BIOS is still intact im fine :P

(thanks for the quick reply)

---

### Post by GuitarRocker2562 on 2008-12-13
What hardware didn't work in Intrepid? Maybe the stuff you need is backported?

---

### Post by Meow27 on 2008-12-13
please i dont want to get into this discussion.... but to answer that, my laptop is a sony vaio vgn-fs980.. ive looked for drivers/patches and such but none of them worked the brightness on interpid is a pain and Wine doesnt work well with it

---

### Post by Meow27 on 2008-12-17
nothing? there has to be *something*
in other news i upgraded clib6 and disabled myself from installing a bunch of dev packages :/

---

