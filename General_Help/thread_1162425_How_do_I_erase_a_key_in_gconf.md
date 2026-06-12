---
title: "How do I erase a key in gconf???"
date: 2009-05-17
forum: General Help
---

### Post by Gotterdammerung on 2009-05-17
Hi, there,

I've installed some programs just to test'em, but not I've uninstalled them. However their keys in gconf still remain. How do I erase them?

Thanks in advance.

---

### Post by mb_webguy on 2009-05-17
Linux doesn't have anything like a registry.  gconf-editor looks a bit like regedit in Windows, but really it's just a convenient way to make edits to numerous text-based configuration files.  If you look in the ~/.gconf directory, you'll notice that it contains files and directories that are identical to the directory structure in gconf-editor.  So if you remove Tomboy notes and want to get rid of the "apps > tomboy" entries in gconf, you just need to delete the ~/.gconf/apps/tomboy directory.

---

### Post by Gotterdammerung on 2009-05-17
It seems that the command below does what I wanted, although its description is somewhat strange.

```
gconftool-2 --recursive-unset /apps/SlabMenu
```

---

### Post by mb_webguy on 2009-05-17
> **Gotterdammerung said:**
> It seems that the command below does what I wanted, although its description is somewhat strange.

```
gconftool-2 --recursive-unset /apps/SlabMenu
```

Yeah, that's basically just a fancy version of "rm -r ~/.gconf/apps/SlabMenu".

---

