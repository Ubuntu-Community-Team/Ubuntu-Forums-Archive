---
title: "Novell evolution"
date: 2009-01-18
forum: General Help
---

### Post by DeltaFee on 2009-01-18
I noticed that I have novel Evolution installed on my Ubuntu and due to the fact that I don't want any novel product on my ubuntu. however, every time I try to uninstall it I can't find it in synaptic package manger and was wondering if any one know how to delete it. Thx

---

### Post by RealPSL on 2009-01-18
You can always run ```
sudo apt-get remove evolution
``` from the terminal.

---

### Post by Bucky Ball on 2009-01-18
Just search for 'evolution' in synaptics. It's right there.

---

### Post by ibutho on 2009-01-18
> **DeltaFee said:**
> I noticed that I have novel Evolution installed on my Ubuntu and due to the fact that I don't want any novel product on my ubuntu. however, every time I try to uninstall it I can't find it in synaptic package manger and was wondering if any one know how to delete it. Thx

AFAIK evolution is now a GNOME app, so I don't think you should really be worried about who develops it. Its really difficult for any Linux user to stay clear of Novell apps or code because they contribute heavily to GNOME, KDE, the kernel, xorg, mono, GTK, openoffice etc.

---

### Post by directhex on 2009-01-19
> **ibutho said:**
> AFAIK evolution is now a GNOME app, so I don't think you should really be worried about who develops it. Its really difficult for any Linux user to stay clear of Novell apps or code because they contribute heavily to GNOME, KDE, the kernel, xorg, mono, GTK, openoffice etc.

Yeah, Ubuntu uses the Go-oo patchset (funded by Novell) so you'd better remove OpenOffice too

And Miguel De Icaza started GNOME, so remove that too

---

### Post by jrusso2 on 2009-01-19
> **directhex said:**
> Yeah, Ubuntu uses the Go-oo patchset (funded by Novell) so you'd better remove OpenOffice too

And Miguel De Icaza started GNOME, so remove that too

Forget Samba too Novell works on that one too.

---

### Post by directhex on 2009-01-19
> **jrusso2 said:**
> Forget Samba too Novell works on that one too.

```
jms@osc-franzibald:/usr/src/linux-source-2.6.27$ grep -ri novell * | wc -l
151
```

And you'd better switch to kfreebsd or hurd

---

### Post by xirtus on 2009-01-19
and you'd better switch to kfreebsd or hurd[/quote]


do it!

---

