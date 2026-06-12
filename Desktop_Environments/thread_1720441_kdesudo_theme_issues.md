---
title: "kdesudo theme issues"
date: 2011-04-03
forum: Desktop Environments
---

### Post by HalfEmptyHero on 2011-04-03
The root theme in kde is reverting to the ugly themeless one. I have already tried linking my ~/.kde folder to /root but it still isn't working. Any suggestions

---

### Post by HalfEmptyHero on 2011-04-03
Ok, I figured it out. I just had to do this:

```
sudo mkdir /usr/lib/qt4/plugins/styles
sudo cp /usr/lib/kde4/plugins/styles/oxygen.so /usr/lib/qt4/plugins/styles/

```

---

