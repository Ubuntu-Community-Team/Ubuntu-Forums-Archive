---
title: "lost cursors"
date: 2006-02-15
forum: Desktop Environments
---

### Post by pataphysician on 2006-02-15
my display was unresponsive and xorg was sucking up system resources, so  made a few changes to my xorg.config file based on a couple of posts here. all i did was add the lines:

        Option          "RenderAccel" "On"
        Option          "NoRenderExtension" "On"
        Option          "Accel" "On"
        Option          "AllowGLXWithComposite" "Off"

after restarting x, my cursors have reverted to default black cursors. i was using the "human" theme previously. when i run gcursor, i see the human theme listed and can preview it, but when i chose it (or any other theme), nothing happens. if i click the, "go to theme folder," button, i'm taken to my .icons folder, but nothing is in it except a folder called BlankOn and a broken link pointing to /usr/share/rox/ROX.

i've looked around at gnome-look and in synaptic, but can't find the theme. how can i get the human cursors back?

---

