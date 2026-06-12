---
title: "Gnome 3D Tetris"
date: 2005-05-20
forum: Gaming &amp; Leisure
---

### Post by kiddyfurby on 2005-05-20
I want a 3D tetris game, I know xbl is in the repositories, but gno3dtet seems nicer

I get an error when I start it after installing the aliened rpm from the site

gno3dtet: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

[http://eseb.net/3dtetris.php?x=3&](http://eseb.net/3dtetris.php?x=3&)

---

### Post by jon_hill987 on 2005-05-21
[QUOTE=kiddyfurby]I want a 3D tetris game, I know xbl is in the repositories, but gno3dtet seems nicer

I get an error when I start it after installing the aliened rpm from the site

gno3dtet: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

[http://eseb.net/3dtetris.php?x=3&](http://eseb.net/3dtetris.php?x=3&)[/QUOTE]

Basicly you need to install the libstdc++.so.6 library.

---

### Post by jon_hill987 on 2005-05-24
[http://rpmseek.com/rpm-pl/libstdc%5C%5C.html?hl=com&cx=0::](http://rpmseek.com/rpm-pl/libstdc%5C%5C.html?hl=com&cx=0::)

download the one for your archetecture, $sudo alien -d /location/file.rpm and then dpkg -i nameofdebgenerated.deb.

It works for me.

---

### Post by jon_hill987 on 2005-05-25
That is one hard game! i can't get past 5 layers on medium setting!

---

### Post by kiddyfurby on 2005-06-03
thx, I don't know about your way, but I have found out the jedi way
o i mean a native way

no rpm, no alien (for the libstdc++.so.6 part)
installing libstdc++6 solved the problem

---

### Post by jon_hill987 on 2005-06-03
[QUOTE=kiddyfurby]thx, I don't know about your way, but I have found out the jedi way
o i mean a native way

no rpm, no alien (for the libstdc++.so.6 part)
installing libstdc++6 solved the problem[/QUOTE]

I assume you managed to find a .deb with it in then, I did a search but could only find that file included in rpm's, the alien just converts to .deb so it can be installed.

---

### Post by kiddyfurby on 2005-06-04
[QUOTE=jon_hill987]I assume you managed to find a .deb with it in then, I did a search but could only find that file included in rpm's, the alien just converts to .deb so it can be installed.[/QUOTE]
its in synaptic

---

### Post by yuki86 on 2009-06-08
hey man just download rpm from here [http://eseb.net/3dtetris.php?c=bow&#downloads](http://eseb.net/3dtetris.php?c=bow&#downloads) and install alien [http://www.howtoforge.com/converting_rpm_to_deb_with_alien](http://www.howtoforge.com/converting_rpm_to_deb_with_alien) and conver rpm to deb):P

---

