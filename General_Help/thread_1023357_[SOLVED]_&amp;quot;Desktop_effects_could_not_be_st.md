---
title: "[SOLVED] &amp;quot;Desktop effects could not be started&amp;quot;"
date: 2008-12-27
forum: General Help
---

### Post by dmillerw on 2008-12-27
Now before you go telling me, "THERES A STICKY ABOUT THIS, Blah blah blah....,) I've already read the sticky, I got the Compiz-Check script and ran it.

```
 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

And here's my compiz command output

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2562 (rev 01) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
/home/dylan/.themes/Clearlooks-DarkNice/gtk-2.0/gtkrc:48: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/dylan/.themes/Clearlooks-DarkNice/gtk-2.0/gtkrc:49: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/dylan/.themes/Clearlooks-DarkNice/gtk-2.0/gtkrc:50: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

```

The strange thing is that it worked about ten minutes ago until I rebooted.

Thanks in advance!

---

### Post by Wartender on 2008-12-27
do you have compizconfig? and maybe you could try using emerald since this appears to be a problem with the window decorator

---

### Post by dmillerw on 2008-12-27
Either I didn't do it right or it didn't help.

I installed Emerald, and I do have compizconfig

---

### Post by dmillerw on 2008-12-27
I rebooted and it started using Emerald.

---

### Post by Wartender on 2008-12-27
ok, glad to have helped :)

---

