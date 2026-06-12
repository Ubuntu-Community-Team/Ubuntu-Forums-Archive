---
title: "how to install shift switcher plugin for compiz-fusion"
date: 2007-09-29
forum: Desktop Effects &amp; Customization
---

### Post by bcdixit on 2007-09-29
hello,
can someone point me to a method to installed the shift switcher plugin for compiz-fusion.
I have installed compiz fusion (git) by using the CF installer script.?


:confused:

thanks
-bcd

---

### Post by bcdixit on 2007-09-29
ok i figured out the method to install plugins from this wiki page.
[http://wiki.compiz-fusion.org/Install/PluginsFromGit](http://wiki.compiz-fusion.org/Install/PluginsFromGit)

but when i try to compile the shift switcher, i get the following error.

> [I]bcdixit@bcdixit-desktop:~/shift$ make
compiling : shift.c -> build/shift.loshift.c:46:25: error: compiz-text.h: No such file or directory
shift.c: In function 'shiftRenderWindowTitle':
shift.c:286: error: 'CompTextAttrib' undeclared (first use in this function)
shift.c:286: error: (Each undeclared identifier is reported only once
shift.c:286: error: for each function it appears in.)
shift.c:286: error: expected ';' before 'tA'
shift.c:313: error: 'tA' undeclared (first use in this function)
shift.c:322: error: 'TEXT_STYLE_BOLD' undeclared (first use in this function)
shift.c:322: error: 'TEXT_STYLE_NORMAL' undeclared (first use in this function)
shift.c:327: error: 'TextRenderWindowTitleWithViewport' undeclared (first use in this function)
shift.c:329: error: 'TextRenderWindowTitle' undeclared (first use in this function)
shift.c:335: error: 'TEXT_ID' undeclared (first use in this function)
shift.c: In function 'shiftInitDisplay':
shift.c:2435: error: 'TEXT_ABIVERSION' undeclared (first use in this function)
make: *** [build/shift.lo] Error 1
[/I]:(

ANYBODY HAVING THE SAME ERROR.

---

### Post by sultanoswing on 2007-09-29
> **bcdixit said:**
> ok i figured out the method to install plugins from this wiki page.
[http://wiki.compiz-fusion.org/Install/PluginsFromGit](http://wiki.compiz-fusion.org/Install/PluginsFromGit)

but when i try to compile the shift switcher, i get the following error.

:(

ANYBODY HAVING THE SAME ERROR.

The CF installer script stopped installing the (cool) shift switcher plugin for me a couple of weeks ago. I also tried compiling in the plugin manually, to no avail. So, I subsequently uninstalled the script and went with Trevino's Repos instead and all is well again.

---

