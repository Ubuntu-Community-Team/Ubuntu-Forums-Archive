---
title: "Gnome-screensaver strange behavior"
date: 2008-06-29
forum: Desktop Environments
---

### Post by UAvron on 2008-06-29
I use a dialog flybook hooked up with a big external screen. After upgrading to Hardy, I have evidently messed up something and ever since then gnome screensaver doesn't seem to work, at least none of the themes I used to have in earlier releases show up, all that happens is that the screen goes blank.
Tried changing the setup values through gconf-editor and set the value of mode to random from blank-only, but it doesn't do a thing.
The only clue I have is that there is not a single screensaver appearing in the list of themes in the config editor, despite having them all in the folder /usr/share/gnome-screensaver/themes and having all the corresponding .desktop files in /usr/share/applications/screensavers.
Alt+Ctrl+L locks the screen correctly
Installing Xscreensaver doesn't help, as Xscreensaver doesn't cover the whole area of the external screen. The proposed workaround doesn't help, thus I need to use gnome-screensaver.
Any ideas?

---

### Post by UAvron on 2008-06-29
Well, problem solved, even though I still don't know what the problem was.
The solution came in the form of the program screensaver-settings.
Download it here: [http://www.getdeb.net/app/screensaver-settings](http://www.getdeb.net/app/screensaver-settings)
It has all the functionality of gnome-screensaver setup and a little more.

---

