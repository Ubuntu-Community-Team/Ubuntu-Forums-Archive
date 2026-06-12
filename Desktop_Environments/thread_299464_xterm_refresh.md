---
title: "xterm refresh"
date: 2006-11-14
forum: Desktop Environments
---

### Post by vermaden on 2006-11-14
xterm does not refresh itself well: 
[http://toya.net.pl/~vermaden/gfx/refresh.png](http://toya.net.pl/~vermaden/gfx/refresh.png) 

But after I hit CTRL+L (manual refresh) everything goes back to normal.

---

### Post by streeto on 2006-11-14
It looks like a problem with font antialiasing. Try using xterm with a fixed font to verify this.

---

### Post by vermaden on 2006-11-14
This is fixed width font already.

---

### Post by streeto on 2006-11-14
Sorry, by fixed font I mean a bitmap font like

XTerm.*.font: 6x13

The font you are using looks like a freetype/scalar/etc font. But then, I may be wrong.

---

### Post by vermaden on 2006-11-14
> Sorry, by fixed font I mean a bitmap font like

XTerm.*.font: 6x13

Yes its TrueType fixed width font, monofur exacly, but I like it very much and do not want to change it.

Maybe there is sollution to this problem without changing my favorite font.

---

