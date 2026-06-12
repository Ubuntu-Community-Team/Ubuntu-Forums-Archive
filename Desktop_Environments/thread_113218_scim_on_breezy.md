---
title: "scim on breezy"
date: 2006-01-05
forum: Desktop Environments
---

### Post by lyly on 2006-01-05
It seems that scim does work very well on breezy (for me at least). When installing it, it just doesn't start (also the configuration from pref menu).

Thus I installed it from packeages at this address [http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/scim/](http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/scim/)
(from this post [http://ubuntuforums.org/showthread.php?t=92303](http://ubuntuforums.org/showthread.php?t=92303))

My problem is that there is no package for scim-m17n and the one in breezy is not compatible with those packages. I need it for entering special caracters like &#257;&#333;&#283;....

Any idea?

---

### Post by kairu0 on 2006-01-05
You should be able to get the same functionality with the uim-m17nlib package, provided you install scim-uim and tell scim to use the uim engine.

---

### Post by lyly on 2006-01-06
Thank you :)  

but I don't understand how to configure scim to use uim...:confused:

---

### Post by kairu0 on 2006-01-06
Run scim-setup, and then under the IM Engines section expand Japanese to show you all of the available Japanese engines. Then, unselect everything except uim.

---

### Post by lyly on 2006-01-06
[QUOTE=kairu0]expand Japanese to show you all of the available Japanese engines. [/QUOTE]

Hem so I have a probleme, because I don't have a Japanese section in this menu....

Here is the list of the packages I installed:
libscim8 
scim-fcitx
scim-gtk2-immodule 
scim-input-pad
scim-modules-socket
scim-modules-table
scim-pinyin
scim-tables-zh
scim-uim
libuim0
uim-m17nlib
uim-utils

Do I missed something? Or maybe is not compatible with the version of scim I download on [http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/scim/](http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/scim/)

Thank you for your help!

---

### Post by kairu0 on 2006-01-06
Oops! What am I saying? You didn't even mention Japanese. My bad.

You are able to get into scim-setup from the console, aren't you? It sounds like you are getting the too-popular scim segfault problem. Have you noticed any segfault error messages yet?

Unless you need m17 functionality in QT applications, then you might do better with UIM (and no SCIM installed.) UIM isn't plagued by the Breezy SCIM problems, so maybe you should give it a try. Try adding the UIM applet to your Gnome panel (right-click -> Add to Panel... -> UIM). Before you do that, though, uninstall all SCIM packages.

Take a look at the screenshot. You can get m17 functionality with UIM.

---

### Post by lyly on 2006-01-07
> **kairu0]Oops! What am I saying? You didn't even mention Japanese. My bad.[/QUOTE]
Should be ok this time  said:**
> 
You are able to get into scim-setup from the console, aren't you? It sounds like you are getting the too-popular scim segfault problem. Have you noticed any segfault error messages yet?

Actually I don't have any segfault with this install (downloaded from the site I metnion above) . But with the packages in Breezy universe, I got a segfault error.

[QUOTE=kairu0]
Unless you need m17 functionality in QT applications, then you might do better with UIM (and no SCIM installed.) UIM isn't plagued by the Breezy SCIM problems, so maybe you should give it a try. Try adding the UIM applet to your Gnome panel (right-click -> Add to Panel... -> UIM). Before you do that, though, uninstall all SCIM packages.
[/QUOTE]
I tried to install the uim packages but then when lauching gedit it craches... Moreover I cannot have any IM in the same dialogue you show on your picture... So maybe I stay with scim because at least smart pinyin works...

---

### Post by kairu0 on 2006-01-07
[QUOTE=lyly]I tried to install the uim packages but then when lauching gedit it craches... Moreover I cannot have any IM in the same dialogue you show on your picture... So maybe I stay with scim because at least smart pinyin works...[/QUOTE]

Are the SCIM packages still installed?

Try opening a console and running gedit. Does it say that it's trying to start a SCIM interface?

---

### Post by lyly on 2006-01-07
[QUOTE=kairu0]Are the SCIM packages still installed?

Try opening a console and running gedit. Does it say that it's trying to start a SCIM interface?[/QUOTE]

No scim package installed (even not libscim8). gedit just crash, no feedback in the console.

well I will maybe stay with the copy past and the special character map applet...

---

### Post by FarEast on 2006-01-07
Hello lyly,

> My problem is that there is no package for scim-m17n and the one in breezy
> is not compatible with those packages. I need it for entering special
> caracters like &#257;&#333;&#283;....

For your purpose, there is a small applet called "Character Palette" which
you can put on upper panel of gnome.
I am using it to input German characters;) .

With KDE, you can switch keyboard layout to languages you want to write.

---

