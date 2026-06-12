---
title: "gtk-qt-engine-kde4 works for all gtk apps *except* Firefox and Thunderbird"
date: 2008-08-09
forum: Desktop Environments
---

### Post by _axiom_ on 2008-08-09
I followed the instructions to install gtk-qt-engine-kde4, and set it up in System Settings.

Gimp and Pidgin look a lot better.

But Firefox and Thunderbird are stuck in 1995 grey box mode.

Note that I am running the official Mozilla packages of FF and TB, rather then the apt-gettable ones, would that cause this?

And no, it is not just the scroll bar.

I did try the  [package from KDE-look]("http://www.kde-look.org/content/show.php/gtk-kde4?content=74689"), but it just came up with errors in my System Settings dialog (could not find some .so file that was really there)

How can I get Firefox and Thunderbird to look beautiful again?

---

### Post by benerivo on 2008-08-09
I think the problem is with you using the downloaded (standalone) version of firefox rather than the repository version. Try installing the rep version, it should look okay. Actually, i have tried firefox in kde4 and the tab bar looks awful, so i wouldn't reccommend it. Anyway, you may be interested in the [qt version of firefox ]("http://www.osnews.com/story/20160/Qt_Port_of_Mozilla_and_Firefox_3")coming soon.

EDIT - I've just tried firefox, downloaded from the mozilla website and it does automatically use the gtk-qt-engine-kde4 settings, so i don't know why it doesn't for yours _axiom_. Although the tab bar looks so bad, you really aren't missing anything. Just wait for the qt version to appear.

---

### Post by _axiom_ on 2008-08-10
Ok, I tried the offical Ubuntu version, and it seems to work, at least the scrollbars are right.  Flash seems to behave less well in this version, but it does work most of the time.

A QT Version of Firefox would be **great**.  Tried running the on they had [here]("http://browser.garage.maemo.org/news/10/"), but got this:
```

./firefox-bin: symbol lookup error: ./libxul.so: undefined symbol: _ZN6QEvent17registerEventTypeEi
```

Hopefully they release one that works soon.

---

### Post by jonnylinuxnerd on 2008-08-19
> **_axiom_ said:**
> 
```

./firefox-bin: symbol lookup error: ./libxul.so: undefined symbol: _ZN6QEvent17registerEventTypeEi
```


I also got the above error whilst testing the exact same release! I am on 64-bit which I think is causing the problem, does anyone know how to fix it?

Thanks!

---

### Post by eagle416 on 2009-01-14
bump! I have the same problem. Why did KDE4 mess up the FF/TB themes?

---

