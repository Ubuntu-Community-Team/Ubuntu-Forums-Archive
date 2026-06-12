---
title: "how to install fonts?"
date: 2005-05-15
forum: Desktop Environments
---

### Post by eewald on 2005-05-15
how do i install fonts in hoary? or, to make it clear, how to make them available for openoffice 1.1. ?

i dragged *.pfb font files (and *.pfm configuration file) fo location fonts:///. 

now, even after restart can all gnome programs use these new fonts, but not the most important one: openoffice. 

how do i install fonts the "old-fashioned" way?

---

### Post by l.tambiah on 2005-05-17
Installing fonts

Not quite sure what you mean by installing the old fasion way, but i will explain how i get my fonts displaying clear.

First step:

Add repositories your sources.list file which is located in the /etc/apt directory. Goto guide at this link of how to do this: 

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Second Step

Install msttcorefonts and gsfonts-x11 if you require (totally your choice), but you will want the msttcorefonts (which are microsoft fonts). Again go to the link of how to do that:

[http://ubuntuguide.org/#extrafonts](http://ubuntuguide.org/#extrafonts)

Third Step

Within the Gnome environment goto System>Preferences>Font

Use your new fonts which should appear, Tahoma or Arial look nice select 10-12 for your text sizes. With the font rendering select Monochrome. Select the "details" button and use either 72 dpi or 96 dpi depending what looks best on your screen, i use 72dpi. Select font smoothing  "OFF". Put the hinting on Medium. Accept the default for RGB and close the dialogue box. 

Open a command promt and type:

killall gnome-panel

You should now see clear fonts in your environment you may want to configure your firefox fonts too by simply going to edit>preferences>general>fonts and colors. Select your required fonts and tick always use your fonts. Close all browser windows and restart firefox.

Hope this is of help to you.

---

### Post by usererror on 2005-05-17
On my Debian system I installed all the windows fonts by copying them off a windows box and then making a folder called **windows** in **/usr/share/fonts/truetype/** and i put them in that folder and then restarted the window manager.  i haven't done it on ubuntu yet but i'm sure it'd work the same. :)

---

### Post by tread on 2005-05-17
I think if you just take the ttf font you want and put it in the .fonts folder in your home directory, it should show up.

---

