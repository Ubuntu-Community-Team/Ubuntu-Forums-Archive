---
title: "Problem with default theme"
date: 2008-12-27
forum: General Help
---

### Post by itchanddino on 2008-12-27
Hi, I already posted this on the [general help forum]("http://ubuntuforums.org/showthread.php?t=1020116"), but so far no one has found a solution.  I figured this might be a better place for this post:

I didn't have this problem before I tried using, and then disabled compiz effects. They're still disabled

Almost every time when I boot, the default Ubuntu theme is this icky one:

[http://i551.photobucket.com/albums/i...ino/stupid.png](http://i551.photobucket.com/albums/i...ino/stupid.png)

I never set it to be this. When I just go into the appearance menu, it automatically goes back to Human without me doing anything:

[http://i551.photobucket.com/albums/i...ddino/nice.png](http://i551.photobucket.com/albums/i...ddino/nice.png)

Is there any way to make Human always be the theme? This is kinda annoying. Thanks

---

### Post by Ivo Moelans on 2008-12-27
I'm really guessing here, but it appears that compiz, although disabled, is still intervening in some way.
You could try this: activate compiz, start *System&#8594;Pereferences&#8594;CompizConfig Settings Manager* and go to *Preferences*. There push the *Reset to defaults* button.

Also, to make sure that Human is really activated:
Open *Applications&#8594;System Tools&#8594;Configuration Editor* (or in terminal type *gconf-editor*). Go to:
1) *apps/metacity/general* and check if in the right pane after the item (key) *theme*, Human is filled in
2) *desktop/gnome/interface* and check item *gtk-theme*

If necessary type Human in those places.

I don't know if this will solve it, but it's worth trying. Let me know how it goes.

---

### Post by itchanddino on 2008-12-28
I did everything you said.  And all the settings already said Human in them.  No luck :(

---

### Post by Ivo Moelans on 2008-12-29
Could you check this:
in *System&#8594;Preferences&#8594;Sessions* under the tab *Startup Programs* there should be an item *GNOME Settings Daemon*. Is it there?

---

### Post by itchanddino on 2008-12-30
Yep, that's there.

---

### Post by Ivo Moelans on 2008-12-30
A complete mystery: your theme is set and the daemon starts upon booting...
The only thing I can think of is that there is something wrong with the theme itself, but Human is fairly straightforward and, provided you have not tinkered with it, it should simply work.
If you would want to make certain it is not the theme itself, you could use some other theme and see if that has the same problem. If it hasn't it's almost certainly a problem with Human. If it has there is something wrong with the system.

Sorry I can't be of more help.

---

### Post by itchanddino on 2009-01-02
If it helps, right after I login it has the Human theme, but then a split second later it goes to that other theme and stays like that until I go to the Appearance Preferences.  Thanks your all your help!

---

