---
title: "Why not have a simple way to turn off recent documents?"
date: 2009-05-08
forum: General Help
---

### Post by Primefalcon on 2009-05-08
I checked around and the only fix I could find is this

[http://ubuntuforums.org/showthread.php?t=66821](http://ubuntuforums.org/showthread.php?t=66821)

the standards chmoding didn't work I had to do

```
rm ~/.recently-used.xbel
touch ~/.recently-used.xbel
sudo chattr +i ~/.recently-used.xbel
```

Why isn't there an easier way to turn this "feature off"? I'm sure there are a lot of other people who would prefer not to have this, not just me

---

### Post by mechdave on 2009-05-08
There is a really quick way of doing it I have found [here. ]("http://ubuntu-snippets.blogspot.com/2009/02/recently-usedxbel-xml-horror.html")In Jaunty all you do is the following in a terminal:

user@userland$] touch ~/.gtkrc && echo gtk-recent-files-max-age=0 > .gtkrc

Then restart gnome by logging out and then back in again. The Recent Documents should be greyed out by now.

Conversley if you wanted to only have say 5 items in recent documents just replace the 0 with a 5 eg:

user@userland$] touch ~/.gtkrc && echo gtk-recent-files-max-age=5 > .gtkrc

log out and then back in again and it should all work...

Happy Linuxing,
Mechdave

---

### Post by Primefalcon on 2009-05-08
oh wow, neat. thx :-D still though there should just be an gtk way to turn this off

---

### Post by mechdave on 2009-05-08
I made a mistake in my post... to limit the number of files to 5 use gtk-recent-files-limit=5 instead of gtk-recent-files-max-age=5 Oops :) The whole docs on sharing settings can be found at [http://library.gnome.org/devel/gtk/stable/GtkSettings.html]("http://library.gnome.org/devel/gtk/stable/GtkSettings.html") if you can read a little of C then you can work out all the settings :)

---

### Post by northwestuntu on 2009-05-18
> **Primefalcon said:**
> oh wow, neat. thx :-D still though there should just be an gtk way to turn this off

i agree!!

---

### Post by le1 on 2010-04-16
The easiest way that worked for me was:

sudo gedit ~/.gtkrc-2.0

-- type in line below:

gtk-recent-files-max-age=0

-- save and done.

ps. make sure to type "files" not "file"

---

