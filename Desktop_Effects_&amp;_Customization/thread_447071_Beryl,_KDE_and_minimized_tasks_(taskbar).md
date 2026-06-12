---
title: "Beryl, KDE and minimized tasks (taskbar)"
date: 2007-05-17
forum: Desktop Effects &amp; Customization
---

### Post by Ateo on 2007-05-17
If I have Program 1 opened on desktop 1 and I have Program 2 opened on desktop 2, both tasks appear in the task bar on every side of the cube.

The options in the "Window Previews" plugin for beryl don't seem to fix the issue.

Is there something I'm missing? This shouldn't work this way right?

---

### Post by Matakoo on 2007-05-17
Sounds like default Kubuntu behavior, but easily changed. Go to control center, desktop, taskbar. Once in that settings module, uncheck "Show windows from all desktops".

---

### Post by Ateo on 2007-05-17
Unchecked option but it still doesn't work. I suspect it's the issue as with the default stock kpager.

---

### Post by Ateo on 2007-05-24
This is solved by using [taskbar-compiz]("http://www.kde-apps.org/content/show.php/taskbar-compiz?content=49484") from kde-apps.org. Another program of interest is [pager-compiz]("http://www.kde-apps.org/content/show.php/kicker-compiz?content=46021").

> Technically, it is a matter of respecting window managers standards as defined by EWMH ([http://standards.freedesktop.org/wm-spec/wm-spec-1.4.html](http://standards.freedesktop.org/wm-spec/wm-spec-1.4.html)), using the facilities already provided by KDE.

---

