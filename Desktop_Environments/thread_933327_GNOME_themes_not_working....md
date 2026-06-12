---
title: "GNOME themes not working..."
date: 2008-09-29
forum: Desktop Environments
---

### Post by Grimhound on 2008-09-29
I'm having an issue where GNOME themes aren't working. They keep flopping out to some ugly default theme. Does anyone know how to fix this?

---

### Post by chucky chuckaluck on 2008-09-29
> **Grimhound said:**
> I'm having an issue where GNOME themes aren't working. They keep flopping out to some ugly default theme. Does anyone know how to fix this?

are your gnome themes stored in you /home/.themes directory? some of the themes i downloaded and placed in that directory didn't work. when i opened up that directory, it appeared that some of the themes were, for want of a better description, "double wrapped". when i took the theme directory out of the wrapper directory and placed it directly in .themes, they worked.

---

### Post by mcduck on 2008-09-29
It could be that you haven't got the GTK2-engine required by the theme. Some engines are installed by default, some can be installed manually from the repositories and some you need to get from other sources (like gnome-look.org).

---

