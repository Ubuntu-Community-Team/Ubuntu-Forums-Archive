---
title: "Disable MATE/Marco compositing by default for all users"
date: 2022-02-09
forum: Desktop Environments
---

### Post by allcoms on 2022-02-09
I'm setting up a 20.04 LTSP server and I've discovered NVIDIA machines can't login to MATE because compositing is enabled by default. If they log into a non-NV box, disable MATE compositing and try again logging into MATE works.

It seems I should be able to disable Marco compositing by editing:

/usr/share/glib-2.0/schemas/org.mate.marco.gschema.xml

Then setting the compositing-manager key to false before running:

glib-compile-schemas /usr/share/glib-2.0/schemas/

but that hasn't worked for me, not even for new users without a home dir / settings.

---

