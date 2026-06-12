---
title: "[SOLVED] Dual monitors no decorations on secondary"
date: 2008-01-04
forum: Desktop Effects &amp; Customization
---

### Post by mylo9000 on 2008-01-04
ok i know there are other threads about this but i cannot seem to get it to work for me.

i found thread that said  to modify the /usr/bin/compiz  to include metacity --replace &  and --only-current-screen  in two locations.

all that did was disable compiz for both screens with metacity. so thats not what i'm after.

if i restore my compiz file from a back up and restart all i have is compiz running on screen 0 and screen 1 (3d effects work for both screens) screen 1 however have no window decorations. and compiz functions with a significant and noticeable delay.

i've also tried a few things with my xorg.conf to no avail.

i have a nvidia geforce 6600LE a 21 inch IBM crt (screen 0) and a Sangyo Nova 15inch wide display (screen 1)

if i could get compiz running on screen 0 and metacity on screen 1 that would be fine.

although i'd rather have compiz running on both displays with window decorations on both.

does anyone have this working at all. i could really use a hand.

thanks in advance.

---

### Post by mylo9000 on 2008-01-05
Found a solution.

on [Forlong's Blog - How to set up Compiz Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion") i found this little tidbit:

"Troubleshooting

No window boarders (titlebars)

Insert the window decorator of your choice (gtk-window-decorator, kde-window-decorator or emerald) in CompizConfig Settings Manager &#8594; Window Decoration &#8594; Command

Additionally for Nvidia users:
Make sure you have a nvidia-glx driver installed and use the following command to configure your xorg.conf:

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

(you have to restart X to make it work) "

so i applied gtk-window-decorator to the command line of the compizconfig settings manager and applied the --add-argb-glx-visuals -d 24 to the nvidia-xconfig and now all works well with compiz on both screens.

hope this helps some one else out there so they don't have to deal with it as long as i have.

---

