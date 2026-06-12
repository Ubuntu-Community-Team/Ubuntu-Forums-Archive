---
title: "Gnome cursors in openbox"
date: 2005-11-12
forum: Desktop Environments
---

### Post by Pixel on 2005-11-12
I wanted to move from gnome to openbox but It doesnt seem to use the same cursors as gnome does...

What do I have to do to make openbox use them?

Thanks.

---

### Post by kelsey23 on 2005-11-12
OpenBox probably does not use Gnome cursors, but I am sure you could get look-a-like cursors or you could even make your own :-)

---

### Post by chombee on 2005-12-16
Pixel - I think you might need to run gnome-settings-daemon when in OpenBox. To do it automatically you could add

gnome-settings-daemon &

to your .xsession file. For details check the OpenBox page on the Ubuntu wiki.

When I ran this program within OpenBox I noticed that it set all my fonts, icons and other things to the same ones used when I login into GNOME. I think I have the same cursor as GNOME too, so it probably does that also.

---

### Post by iced-tux on 2005-12-29
Sure it does...
If you start the gnome-session you HAVE practically gnome up and running.
The only thing that has changed is your WM: Metacity --> Openbox.
But if you want to run a pure openbox .... 
Well I haven't found a solution to the x-cursor problem :(

---

### Post by iced-tux on 2005-12-29
Well I found a kind of solution for your cursor problem.
Try adding:
Xcursor*theme: <NameOfYourFavoriteCursorTheme>
to your .Xdefaults.

---

