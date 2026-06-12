---
title: "Can rhythmbox prevent suspend?"
date: 2009-05-11
forum: General Help
---

### Post by sgardne on 2009-05-11
I'd like to be able to have Ubuntu not go into sleep mode while rhythmbox is playing. Is there a way to make this happen?

-Scott

---

### Post by sgardne on 2009-05-13
Well I figured this out for anyone who cares. Press Alt+F2 type in "gconf-editor", without the quotes. Go to "apps>rhythmbox>plugins>power-manager", check the "active" checkbox. Quit gconf-editor. Open Rhythmbox. Go to "Edit>Plugins". Check the box for "Power Manager".

IMO, this should be an active and visible plugin by default, and maybe it should just not be enabled. ):P

---

### Post by namd3r on 2009-05-13
I thought it already came as a visible plugin?

---

