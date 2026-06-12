---
title: "lost my window themes after installing beryl"
date: 2007-06-25
forum: Desktop Environments
---

### Post by mpneerkaje on 2007-06-25
Hi there,

I'm running ubuntu 7.04 on AMD 64 X2(Asus M2N-MX). After I installed xgl and beryl, my gnome thems are missing. It has been quite annoying to work without these, though all other beryl features are working fine. How can I get back my themes?

I have also installed emerald theme manager. There is no use changing settings there, as the selected themes are not visible.

Any help from you folks?

Thanks in advance,
Mahesh

---

### Post by Happy_Man on 2007-06-25
Press Alt+F2 and run ```
emerald --replace
```

---

### Post by mpneerkaje on 2007-06-26
> **Happy_Man said:**
> Press Alt+F2 and run ```
emerald --replace
```

I did that but didn't help. Just to put some more light on the problem - The window title is missing. I'm able to move/maximize using ALT+Right click. So only thing missing is window title and frame. How silly is this? :(

Any help friends?

Regards,
Mahesh

---

### Post by mpneerkaje on 2007-06-26
Also, is there any problem if compiz is installed in the system along with beryl?

I was searching extensively for the solution, i found somebody told this:
compiz --replace, followed by emerald --replace,

it gave me the following error:

[COLOR="DarkOrange"]compiz --replace&[/COLOR]
/usr/bin/compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
inotify_add_watch: No such file or directory

[COLOR="DarkRed"]emerald --replace&[/COLOR]
No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32


Any suggestions?

Regards,
Mahesh

---

