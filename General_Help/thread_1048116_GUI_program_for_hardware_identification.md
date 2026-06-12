---
title: "GUI program for hardware identification"
date: 2009-01-23
forum: General Help
---

### Post by Pidgin on 2009-01-23
I remembered that there was a GUI program that could show information of hardware in 7.10. But it was gone since 8.04. Can anyone tell me what that program is called and how to install it?
Thank you!

---

### Post by theozzlives on 2009-01-23
Device Manager in Add/Remove Programs

---

### Post by Pidgin on 2009-01-23
> **theozzlives said:**
> Device Manager in Add/Remove Programs

Oh, thank you very much! It's the package [FONT="Monospace"]gnome-device-manager[/FONT].

---

### Post by hyper_ch on 2009-01-23
```

sudo lshw -html > ~/Desktop/hardware.html

```

---

### Post by Pidgin on 2009-01-23
> **hyper_ch said:**
> ```

sudo lshw -html > ~/Desktop/hardware.html

```

That looks good, too. Thanks!

---

### Post by stalkingwolf on 2009-01-23
Yep. Gnome device manager.  after install it will be (or should be under
applications > system tools)

---

### Post by Pidgin on 2009-01-23
I find a problem that those tools are relatively old. Fear that they are unable to identify new hardware properly.

---

