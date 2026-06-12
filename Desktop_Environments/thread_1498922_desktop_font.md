---
title: "desktop font"
date: 2010-06-01
forum: Desktop Environments
---

### Post by rplantz on 2010-06-01
The characters labeling the (gnome) desktop icons are white with shading. Is there any way to change them so that they are simply solid?

I can use System->Appearance to change the font family, size, and style, but there does not seem to be a way to change its color and shading.

---

### Post by sedawk on 2010-06-07
Similar issue here, I changed the background to a light color and
now the font is nearly unreadable.

Here is the solution I found:

* install gnome color chooser ("sudo apt-get install gnome-color-chooser")
* select panel "Desktop"
* below section "Icon Labels" mark check box beautify icon labels
* mark the check box for normal text and change it.
* press the apply button to check readability.

I wonder if there is some decent magic to automate something like this,
e.g. by checking the brightness (?) of the background color. Might
need more tuning when a gradient is used, or a colorful image.

---

### Post by rplantz on 2010-06-07
Wow, thank you, sedawk!! Exactly what I have been looking for. BTW, I also marked the "Background Opacity" check box and set the opacity to 0.

I also think this should be much simpler. Surely we are not the only two Ubuntu users who would like to do this. :-)

---

### Post by sedawk on 2010-06-08
Luckily we are using Ubuntu, where the gnome color chooser is
part of the distro.

I'm also running Fedora 13 and I couldn't find it in any
of the Repos, so I had to compile it myself. Worked fine,
but with lots of dependencies missing this takes much more
time than simply installing an existing package.

---

