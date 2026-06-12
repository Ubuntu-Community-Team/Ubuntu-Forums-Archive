---
title: "gnome shell brightness, volume overlay transparency bug"
date: 2012-12-26
forum: Desktop Environments
---

### Post by gexi on 2012-12-26
hey there,

i'm using gnome shell on a standard 64bit quantal installation with gnome3-team ppa. the theme is faience from tiheum equinox ppa (but the problem also occurs with the standard gs-theme).

as you can see in the screenshot, the volume overlay is not rendered correctly (same thing with brightness). i thought this is a problem with the faience-theme (or that it was maybe intended to be that way), but today i found out, that the bug occurs for every shell theme i try.

btw. every other transparent thingy is rendered correctly.


would be greatly appreciated if someone had any idea how to solve this.

thanks in advance.

---

### Post by gexi on 2012-12-27
Ah, strange!

Just found out: it's got something to do with the *gtk+ theme* (not the shell-theme as i thought before). if i change the gtk+ theme to the adwaita default theme, those transparent overlays are rendered correctly.

So, the problem occurs with the following gtk-themes: *faience, ambiance, radiance* ... (i haven't installed that many though).

Does anybody know if those themes got any packages in common, maybe from gnome3-team or equinox repos?

---

### Post by Morphine. on 2013-01-14
I'm having the exact same problem!
are you any closer to a solution?

---

### Post by NikiNfOuR on 2013-01-15
I am also having the same problem. Have to adjust the brightness every time boot up the OS. Hoping to find a solution soon..

---

### Post by Morphine. on 2013-01-15
I've been having a look around, and it seems to be a problem with the theme code.
It would appear that the theme developers have neglected to add a style entry for the meda-key's OSD

I was able to mend the theme i'm currently using (zoncolor) by adding some lines to the gtk.css

Here are the changes made to the Evolve theme to fix this issue 
[https://github.com/satya164/Evolve/commit/b467d14ebd2b53bbb908e207c78065ddd4dff646](https://github.com/satya164/Evolve/commit/b467d14ebd2b53bbb908e207c78065ddd4dff646)

I hope this helps

---

### Post by cmcanulty on 2013-01-16
this works for me. It is super dumb that keeping the set level isn't the default!
[http://askubuntu.com/questions/93038/lenovo-laptop-dims-always-on-reboot]("http://askubuntu.com/questions/93038/lenovo-laptop-dims-always-on-reboot")

---

