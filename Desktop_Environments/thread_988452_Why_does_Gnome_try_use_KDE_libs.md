---
title: "Why does Gnome try use KDE libs?"
date: 2008-11-20
forum: Desktop Environments
---

### Post by pickarooney on 2008-11-20
When I run firefox or any other browser in Gnome, it outputs error messages to the effect that it can't load some KDE components:

```

/usr/lib/libkdeui.so.4: undefined symbol:
_ZN7KGlobal23unregisterStaticDeleterEP18KStaticDeleterBase
/usr/lib/kde3/plugins/styles/baghira.so could not be unloaded

** (galeon:17724): WARNING **: I could not load the bookmarks file, will
load the default bookmarks from
/usr/share/galeon/default-bookmarks.xbel.

** (galeon:17724): CRITICAL **: radio_group_set_from_value: assertion
`action != NULL' failed
galeon: symbol lookup error: /usr/lib/libkdeui.so.4: undefined symbol:
_ZN7KGlobal23unregisterStaticDeleterEP18KStaticDeleterBase
```

Any idea why that would be or how I could fix it?

---

### Post by aysiu on 2008-11-21
I don't think you'll find the solution to this problem.

I did [a Google search on part of your error message](http://www.google.com/search?hl=en&q=%2Fusr%2Flib%2Fkde3%2Fplugins%2Fstyles%2Fbaghira.so+could+not+be+unloaded++&btnG=Google+Search). It turned up only 17 results, and no working solutions.

---

