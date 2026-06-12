---
title: "compiz: disable window preview on tabbing apps (Alt+Tab)"
date: 2009-07-20
forum: Desktop Environments
---

### Post by manolo_asdf on 2009-07-20
hi,

i am using Alt+Tab for changing windows on a workspace. compiz is enabled and while tabbing through the apps i want to switch the window preview off (displaying the app symbol is just enough).

i tried to find the setting inside config-app compizconfig-settings-manager, but no success. maybe i overlooked this setting?

---

### Post by komputes on 2009-07-20
It could be any of the following compiz plugins:

[http://wiki.compiz-fusion.org/Plugins/Switcher](http://wiki.compiz-fusion.org/Plugins/Switcher)

---

### Post by manolo_asdf on 2009-07-20
thanks, but still I cannot find the disable thumbnail option (see screenshot). I only can disable the icons but these I want to keep.

---

### Post by Dragon45 on 2009-08-20
*bump* any luck? This is my number one beef with compiz at the moment.

I can't find anything in the regular Application Switcher for this either.

---

### Post by telengard on 2010-05-02
Ditto, this is my only issue w/ the alt tabbing (w/ the static switcher).  I'd just like icons.

---

### Post by romwell on 2011-03-30
Bump.

It's almost April 2011, and yet there's still no option to disable the thumbnails.

Most of my windows are some text on white background. It's takes me a second or so to tell apart the browser, text editor, file manager, book reader, etc., since they all are pretty much white rectangles. Having a small screen (10 inch netbook) really does not help.

What I want is small icons only, like in metacity. However, I do want to use compiz, since for some reason it runs much faster than metacity on my machine.

Going to submit it to the 100 paper cuts list later, but I hope that somebody else does it for me :)

---

### Post by Krytarik on 2011-03-30
@romwell: Unfortunately, that's still not possible. But if you enable compositing for Metacity, you should get a much better performance with those. To do so, just run this command:
```
gconftool-2 /apps/metacity/general/compositing_manager --type bool --set true
```But I could understand it, if you don't want to give up the eyecandy and the special features that Compiz offers.

Greetings.

---

### Post by Copper Bezel on 2011-03-30
You might consider one of the other options - the Shift Switcher's previews are almost full-size, so it's easy to tell windows apart. I use the Ring Switcher, which sort of splits the difference between the two (although it's a rather bewildering visual at first.)

---

