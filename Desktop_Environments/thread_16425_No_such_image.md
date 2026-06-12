---
title: "No such image"
date: 2005-02-21
forum: Desktop Environments
---

### Post by watje on 2005-02-21
many programs doesn't work anymore because they can't find a image anymore

with thunderbird:
** ERROR **: No such image: scroller-v-trough.png

synaptic & firefox:
** ERROR **: No such image: progressbar_trough.png

and many others. So i'm currently writing this in dillo ;x

when i did 'locate progressbar_through.png' i got this:
/usr/share/eazel-engine/progressbar_trough.png

it was a while ago befor i did locate -u. So I installed gtk-eazel etc. but it still doesn't work. Does someone know how to fix this? Thanx _VERY_ much!

---

### Post by watje on 2005-02-21
full error when i launch totem:
> (totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/media-player-48.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `icon'

(totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/stock-tool-brightness-contrast-22.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/stock_media_previous.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/stock_media_play.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/stock_media_next.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/rhythmbox-volume-zero.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/rhythmbox-volume-max.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/media-player-48.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `icon'

(totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/media-player-48.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `icon'

(totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/playlist-16.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/stock_media_previous.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/stock_media_play.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/stock_media_next.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/playlist-24.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/rhythmbox-volume-zero.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/rhythmbox-volume-max.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(totem:25951): Gtk-WARNING **: Error loading icon from file '/usr/share/totem/media-player-48.png':
        Couldn't recognise the image file format for file '/usr/share/totem/media-player-48.png'

** (totem:25951): WARNING **: Couldn't find themed icon for "stock-media-play"

** (totem:25951): WARNING **: Couldn't find themed icon for "stock-media-pause"

** (totem:25951): WARNING **: Couldn't find themed icon for "stock-media-prev"

** (totem:25951): WARNING **: Couldn't find themed icon for "stock-media-next"

** (totem:25951): WARNING **: Couldn't find themed icon for "panel-screenshot"

** (totem:25951): WARNING **: Couldn't find themed icon for "stock_playlist"

(totem:25951): libglade-WARNING **: Error loading image: Couldn't recognise the image file format for file '/usr/share/totem/media-player-48.png'

(totem:25951): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `icon'

---

### Post by kassetra on 2005-02-21
first of all, what theme are you using?
 (Computer->Desktop Preferences->Theme)
 
 If you try switching to another theme and running totem do you get the same problems?
 
 second, is this a fresh warty install?

---

### Post by watje on 2005-02-22
I can't switch to another theme like that, because that program also wo'nt open. 
Maybe there is a text-mode way (let's hope so). And it's not a fresh install. 
Thnx

---

### Post by kassetra on 2005-02-22
[QUOTE=watje]I can't switch to another theme like that, because that program also wo'nt open. 
Maybe there is a text-mode way (let's hope so). And it's not a fresh install. 
Thnx[/QUOTE]

Yes, there is a text-mode way:

1. Open a terminal
2. type the following and press enter:
 ```
gconf-editor
``` 
3. Navigate through the tree on the left to: desktop->gnome->interface
4. You change the "icon theme" by typing in another theme name.  (check /usr/share/icons for a list of themes)
5. click your mouse off of the theme name to "set" your changes.
6. close the editor.
7. if the changes aren't immediate, log out & log back in.

---

### Post by watje on 2005-02-22
[QUOTE=kassetra]first of all, what theme are you using?
 (Computer->Desktop Preferences->Theme)
 
 If you try switching to another theme and running totem do you get the same problems?
 
 second, is this a fresh warty install?[/QUOTE]

I can launch the program and click on desktop, but when i click on gnome the program terminate with this error:
** ERROR **: No such image: scroller-v-trough.png

:x

---

### Post by kassetra on 2005-02-22
[QUOTE=watje]I can launch the program and click on desktop, but when i click on gnome the program terminate with this error:
** ERROR **: No such image: scroller-v-trough.png

:x[/QUOTE]

Ok, let's do this the really manual way.
1. You need to know the name of the theme you're going to change to (look in /usr/share/icons and pick out a theme name) - keep the name of that theme directory handy!
2. Open a terminal or go to a terminal window and type in this command (replacing THEME withe the exact theme directory name you found in step 1)
 ```
cp /usr/share/icons/THEME/index.theme /home/username/.icons
```
Notice that we're not using sudo on this command!  If you use sudo, you'll lock yourself out of your .icons directory.
3. It should be fixed immediately, but if not, log out & log back in.

If you do lock yourself out, or if the copy gives you a permissions error, let me know, and I'll help you.

---

