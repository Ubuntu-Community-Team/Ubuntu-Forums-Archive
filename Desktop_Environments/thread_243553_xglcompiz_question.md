---
title: "xgl/compiz question"
date: 2006-08-25
forum: Desktop Environments
---

### Post by buckweat420 on 2006-08-25
Hello,
I was wondering if there was anyway to make the maximize and unmaximize wobble effect faster or not happen at all? Thanks!

---

### Post by vavoem on 2006-08-25
You can change the settings of your effects with the gset-compiz command click on the plugin button at the top and you'll find you can speed or slow things down and much other really cool features.

---

### Post by _profox on 2006-08-25
> **vavoem said:**
> You can change the settings of your effects with the gset-compiz command click on the plugin button at the top and you'll find you can speed or slow things down and much other really cool features.

gset-compiz is very outdated though -- could even be you don't have it if you recently installed compiz

You can change all the options through gconf-editor:

Type in the terminal:
**gconf-editor**

And go to:
**apps --> compiz -->**

There you'll find options for all the plugins -- for wobbly you can click
**apps --> compiz --> plugins --> wobbly --> ...**

---

### Post by tribaal on 2006-08-25
If you're, like me, annoyed by the wobbling and would like to disable it completely, the easiest way to do that is to desactivate the plugin totally:

gconf-editor
Apps > Compiz > General > Allscreens > Options
The first item in the right pane is active_plugins
Remove wobbly from the list there.

You'll never see a wobble again :) This was making me seasick :( Although it had a pretty strong mesmerizing effect on my Windows-using colleagues :)

- trib'

---

### Post by buckweat420 on 2006-08-25
Thanks for everyones help! I went ahead and disabled it. Kinda makes me sea sick too :S All the other features are kool, just that one was :S

---

