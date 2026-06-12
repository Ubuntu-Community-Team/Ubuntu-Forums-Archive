---
title: "how to update my battle for wesnoth"
date: 2008-10-27
forum: Gaming &amp; Leisure
---

### Post by uselessname on 2008-10-27
...guys..need help here..i've already installed battle for wesnoth v1.2.6 through synaptic package manager..but i saw a newer version released w/c is  v1.4.5 at [http://getdeb.net]("http://www.getdeb.net/app.php?name=The+Battle+for+Wesnoth")..

..my problem is i don't know how to update the game..any ideas,reactions,suggestions??!!

tenx ..

---

### Post by ad_267 on 2008-10-27
You can download the .deb files from getdeb and install them just by double clicking on them. This will update your previous install. Unless there's some new features you really want it's recommended to stick with the version from the Ubuntu repos. You will probably have to install the "wesnoth" package last (after wesnoth-data etc) because it depends on these packages.

---

### Post by Ozor Mox on 2008-10-27
If you wait until the new Ubuntu version is out in a few days and upgrade, Wesnoth will be upgraded by the package manager automatically. If you don't want to upgrade Ubuntu, I would recommend uninstalling Wesnoth using Synaptic and then install the newest version from GetDeb, or compile it yourself. GetDeb is the simplest method, but compiling is also dead easy if you do it right.

---

### Post by Perfect Storm on 2008-10-27
Guide to install wesnoth latest 1.5.5 (remember to uninstall previous first).
[http://gaming.gwos.org/doku.php/guides:64bit:battle_for_wesnoth](http://gaming.gwos.org/doku.php/guides:64bit:battle_for_wesnoth)

---

### Post by uselessname on 2008-10-27
..thanks guys!!!:D:)
.big big thanks.now i can be in my game addiction mode...

...by the way is the v1.5.5 stable in v7.10 ubuntu?!

---

### Post by ad_267 on 2008-10-27
You mean Ubuntu 8.10?

No 8.10 only has Wesnoth 1.4.5 (same version as getdeb)

---

### Post by Perfect Storm on 2008-10-27
1.5.5 is unstable (development) but it works great nevertheless.
1.4.5 is stable.
of wesnoth.

---

### Post by uselessname on 2008-10-28
aie..is that so..well anyway thanks again for the help..

@ad_267: no, not v8.10 ubuntu..i'm still stuck w/ v7.10 ubuntu (i'm switching to 8.04 first,a clean install, and maybe that time the 8.10 is already out) that's why i've downloaded an older version..and why,also,i've asked AI if v1.5.5 is stable..though i did not mention my current version of ubuntu..anyway thanks for the idea.. :):p

---

### Post by uselessname on 2008-10-28
..another problem here
i've installed the packages of wesnoth 1.4.5 but the others don't

Here's the packages that i've already installed:

wesnoth 1.4.5 music
wesnoth-data 1.4.5

and here's the list w/c i am not able to install due to some errors:

wesnoth editor 1.4.5       
error: Dependecy is not satisfiable: libboost-iostreams1.34.1

wesnoth campaign 1.4.5
error: Dependency is not satisfiable: wesnoth

wesnoth server 1.4.5
error: *same as wesnoth editor*

and lastly,
wesnoth 1.4.5
error: *also same as wesnoth editor*

..what should i do now??..any suggestions..:)

---

### Post by Perfect Storm on 2008-10-28
Check synaptic and see if libboost-iostreams have the required X.X.X version. It might be that Gutsy are using an old version of libboost-iostreams.

---

### Post by uselessname on 2008-10-28
..i've checked the synaptic and searh for "libboost-iostreams",then it resulted to libboost-iostreams1.34.1 and libboost-iostreams-dev..i've installed this too..still nothing happen, same error as it was..am I doin g something wrong here..:confused:

hope you can enlighten me....

---

### Post by Perfect Storm on 2008-10-28
Strange...maybe there's an error with the .deb packages. You could compile instead.

---

