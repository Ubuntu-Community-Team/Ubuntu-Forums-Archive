---
title: "Ubuntu Minimal + XFCE 4.4.3 (Backports)..."
date: 2009-01-07
forum: Desktop Environments
---

### Post by adamlau on 2009-01-07
...with Thunar 0.9.92 from Xfce 4.6 Beta 2 (Hopper) is flying fast :D . Thunar is noticeably quicker on startup and directory load time than the default 0.9.3 build. Nice and stable (so far) as well. The key is to install Thunar according to the [Xfce Build Order](http://wiki.xfce.org/releng/4.6/general-info#build_order) list. I had to uninstall xfce4-panel as it was not working after restarting Xfce, hope all goes well for you guys interested in a super speedy Thunar. Here are my build options:

```
./configure --disable-wallpaper-plugin --disable-dependency-tracking --disable-tpa-plugin --disable-apr-plugin --disable-pcre --disable-sbr-plugin --without-html-dir --disable-dependency-tracking --disable-nls --enable-debug=no --disable-debug --disable-checks --disable-profiling --enable-final CFLAGS="-march=native -O2" CXXFLAGS="${CFLAGS}"
```

Only UCA was enabled, otherwise the build is minimal. Good luck :popcorn: .

---

