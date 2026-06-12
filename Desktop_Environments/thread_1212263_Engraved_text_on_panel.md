---
title: "Engraved text on panel?"
date: 2009-07-13
forum: Desktop Environments
---

### Post by Fzang on 2009-07-13
In my window border theme I find this:

```
<draw_ops name="title-text-focused">
<title color="#d6d6d3" x="(width - title_width) / 2 +0" y="(height - title_height) / 2 + 1"/>
<title color="#000000" x="(width - title_width) / 2" y="(height - title_height) / 2"/>
</draw_ops>
```

This draws a black title on top (#000000) and a light grey title below (#d6d6d3). The 2+1 says that the light grey text is moved 1px down, causing an illusion that looks like the title is engraved into the titlebar.

[img]http://i27.tinypic.com/33yiz9j.png[/img]

Now my question, is it possible to apply the same effect to the panel? Possibly through gtk-rc?

---

