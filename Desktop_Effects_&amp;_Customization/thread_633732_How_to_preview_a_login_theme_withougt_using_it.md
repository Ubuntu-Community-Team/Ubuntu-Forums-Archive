---
title: "How to preview a login theme withougt using it?"
date: 2007-12-06
forum: Desktop Effects &amp; Customization
---

### Post by B-Con on 2007-12-06
When developing a login theme, is there a way to preview your theme without installing it, logging out, and viewing it? Doing so can be quite a pain, as you can imagine, when you're tweaking the final visual details.

---

### Post by jairtrejo on 2007-12-06
You might be interested in Xnest. Xnest is an X server that shows its output in a window, rather than in the full screen. That's quite usefull for many applications, but in your case, you can install the theme, and then launch the gnome desktop manager with xnest as it's target server to preview it.

For installing, just type in a terminal:
```

sudo apt-get install xnest
```

For executing the gnome desktop manager:
```

gdmflexiserver --xnest
```

As easy as that, a window will pop up showing the theme you most recently installed.

---

### Post by B-Con on 2007-12-09
Ah, very nice, that's a life saver. Thanks.

---

