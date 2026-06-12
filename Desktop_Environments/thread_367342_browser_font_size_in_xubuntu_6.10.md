---
title: "browser font size in xubuntu 6.10"
date: 2007-02-22
forum: Desktop Environments
---

### Post by jeisma on 2007-02-22
hello!

i want to reduce the font size in xubuntu 6.10. i do that by going to settings manager-user interface preferences.

however, i noticed that the browser (opera and/or firefox) fonts in menu bar, toolbar, address bar doesnt change. it annoys when you switch windows you have one that is a bit different. thunderbird is fine.

anyone have any idea how to go around this?


thanks!

joey

---

### Post by kerry_s on 2007-02-22
You can do firefox with a userChrome.css, just go into ~/.mozilla/firefox/?.default/chrome
open up the userChrome-example.css and put this on the bottom->

* {
font-family: Sans-Serif !important;
font-size: 12px !important;
}

You can select your font and size you want to use, use the file> save as userChrome.css

---

