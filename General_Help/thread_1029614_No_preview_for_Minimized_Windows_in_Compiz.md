---
title: "No preview for Minimized Windows in Compiz"
date: 2009-01-03
forum: General Help
---

### Post by cdahmedeh on 2009-01-03
Hello,

I've noticed that there is no window preview when alt-tabbing for minimized Windows. All I see is their icon. Is there anyway to remove this limitation?

Thanks

---

### Post by haran_hockey on 2009-01-03
I don't think you can see the preview of windows when minimized. It's kind of like how you can only expose windows that are not minimized. I think this is s limitation in ubuntu and it uses a lot more resources if ubuntu can do this.

---

### Post by amauk on 2009-01-03
the information needed to query windows is destroyed once a window is minimized

I believe this is being addressed in X-server 1.6
which will ship with jaunty

---

### Post by davewantsmoore on 2009-01-23
and I can't wait :-D

---

### Post by uBeer on 2009-01-23
I believe it's not a X-server issue, more a gnome/metacity issue. Metacity stops rendering a minimized window altogether so it saves processing power.

I also believe it is not a X-server issue because KWin in KDE4 can handle it.

---

