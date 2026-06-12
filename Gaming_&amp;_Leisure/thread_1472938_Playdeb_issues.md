---
title: "Playdeb issues"
date: 2010-05-04
forum: Gaming &amp; Leisure
---

### Post by keljaden on 2010-05-04
I followed all of the instructions on playdebs site and I get the error

"invalid package name"

I am running Linux Mint 8 XFCE (based on ubuntu 9.10)
(brand new install)

browser is firefox

 
how do I fix this error?

---

### Post by Bölvaður on 2010-05-04
did you add the playdeb repo?

*added*
download [this package]("http://archive.getdeb.net/install_deb/playdeb_0.3-1%7Egetdeb1_all.deb") and open it. it will set everything up for you so the apt links on playdeb will work

---

### Post by lessmemorelove on 2010-05-04
delete your playdeb getdeb repo entries

install the getdeb repo deb 

[http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb]("http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1%7Egetdeb1_all.deb")

edit the getdeb entry for either "apps" or "games" or "apps games" for both without the quotes

edit: whoops. that's what you get when you open too many tabs. somebody beat me to the answer :)

---

### Post by keljaden on 2010-05-04
I removed my old entry and used your .deb installer.  I tried again and I receive the same message.

---

### Post by hikaricore on 2010-05-04
Then you're doing something wrong.
I suggest installing games via a package manager using the get/playdeb repos instead of the web interface.

---

### Post by keljaden on 2010-05-05
thx guys, i just install it from the repos and it works great... for some reason playdeb works in mint KDE, but the getdeb repos don't...I get an error when I try to enable them.  I know there is a bug, but that is kinda crazy.

---

