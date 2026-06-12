---
title: "Stop enlarging of icons in nautilus &quot;icon view&quot;"
date: 2009-05-24
forum: General Help
---

### Post by svivian on 2009-05-24
If I use "icon view" in Nautilus, large images are thumbnailed nicely. However, very small images - i.e. 16x16 icons - are ENLARGED to fit the current thumbnail size.

It looks horrible (see attachment). And when images are that small you just want to display them at their natural size!

How can I stop these images enlarging? I've searched every option I can find. Even the smallest zoom nautilus allows still enlarges and blurs the images.

---

### Post by Minsky on 2009-05-24
Open a terminal window and type:

**gconf-editor**

In the left hand sidebar in the window that opens go to **apps > nautilus > icon_view**. A list of keys will be displayed in the large right hand pane, double click on **thumbnail_size** and enter a suitable size in the **value** box. Click **OK** and close the editor, you'll probably need to find the ideal size your screen resolution through a bit of trial and error, try a value of 40 as a starting point.

---

