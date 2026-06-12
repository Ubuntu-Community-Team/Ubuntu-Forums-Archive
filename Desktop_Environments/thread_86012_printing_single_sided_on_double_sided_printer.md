---
title: "printing single sided on double sided printer"
date: 2005-11-04
forum: Desktop Environments
---

### Post by RikoW on 2005-11-04
Hi,

is there an (undocumented?) option, how I can force a printer to print a file single sided instead of the default double sided?

I'm looking for something along the line

```

> lpr --simplex file.ps

```
The man page doesn't give any option for that.

Thanks,
              Riko

---

### Post by dcstar on 2005-11-04
[QUOTE=RikoW]Hi,

is there an (undocumented?) option, how I can force a printer to print a file single sided instead of the default double sided?
.......[/QUOTE]
You may be able to install another instance of the same Printer on the same port (with a different name), but set its properties as Single-sided, and just select that when you need it.

---

### Post by Joe_lurker on 2005-11-04
Try: 

```
lpr -o sides=one-sided file.ps
```

It's not undocumented; load the file 'file:///usr/share/cups/doc-root/index.html' in your favorite browser.

-Joe

---

### Post by RikoW on 2005-11-07
Thanks guys!

Both of the above methods work! 

In the printer configuration window of gnome, you need to turn the double-sided option off. To bad only, that the dialog doesn't let you set your own name for the printer. Instead you have to edit 

```
/etc/cups/printers.conf
```

by hand and rename the printer file in 

```
/etc/cups/ppd
```

Cheers,

            Riko

---

