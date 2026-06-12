---
title: "I miss the Development metapackage"
date: 2009-01-08
forum: General Help
---

### Post by Abraxis on 2009-01-08
So I've been distro hopping for the last 2 months or so.  In my exhaustion I have decided to rest in Ubuntu for a while since it does suit most of my needs.

there is one major problem though in that there is no "Development Metapackage" like in Mandriva, SUSE and some of the others.

Now I'm trying to compile wine from source (I have to patch the source code so installing the binaries from aptitude is out of the question).

While I'm ./configure(ing) I'm getting error after error telling me "SuperWidgetLib32 could not be found.  You could continue without supporting it.... buuuuuut your house would probably collapse and your girlfriend would leave you."
So I go off on some Odyssey into the synaptic package manager, randomly clicking on everything that seems like it might be what I need, install them, and try again.
Success! I've made it passed SuperWidgetLib32! but now it tells me I need the Gnome-FluxCapacitor libraries. :confused:

I'm running the AMD64 architecture, and I'm sure I just need all the 32bit libraries.  But I'm no professional I've only been playing around with linux for about 2 months.  

So is there any way for me to easily acquire all of the stuff I would need to compile from source with 32bit support or whatever?  or maybe even like, a shopping list of things for me to apt-get install?

---

### Post by dcstar on 2009-01-08
> **Abraxis said:**
> So I've been distro hopping for the last 2 months or so.  In my exhaustion I have decided to rest in Ubuntu for a while since it does suit most of my needs.

there is one major problem though in that there is no "Development Metapackage" like in Mandriva, SUSE and some of the others.
.....

build-essential

---

### Post by Abraxis on 2009-01-08
Yes I've tried that already

```
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Maybe because 32bit libraries aren't considered essential for a 64 bit architecture?

one of the missing development files is "FreeType 32-bit development files" so the fonts can't be built... I just --without-freetyped(ed) that one.

once the ./configure finnishes, the last seciton is flooded with
```

configure: XShape 32-bit development files not found, XShape won't be supported.
configure: libXxf86vm 32-bit development files not found, XFree86 Vidmode won't be supported.
configure: WARNING: libxml2 32-bit development files not found, XML won't be supported.
```

and about 4 dozen other such warnings. all with "32-bit development files" in the name.

---

### Post by Cracauer on 2009-01-09
Ubuntu doesn't have much of a 32 bit compat environment for runtime in the first place. They have some, but not nearly as extensive as Fedora.

If you are serious about 32 bit development on 64 bit Ubuntu ot Debian I recommend working in a chroot.

---

