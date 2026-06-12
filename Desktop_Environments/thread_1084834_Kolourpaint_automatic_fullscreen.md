---
title: "Kolourpaint automatic fullscreen"
date: 2009-03-02
forum: Desktop Environments
---

### Post by nathand28 on 2009-03-02
I have installed Kolourpaint in Gnome, and recently whenever I start it or open a new file it automatically goes to fullscreen. I can change it in the settings sometimes, but sometimes it crashes my computer but I can just press ctrl alt backspace.
 Is there a way to fix this or is there another graphics program that has the same functionality as Kolourpaint but is easier to use than GIMP ?

---

### Post by nathand28 on 2009-03-07
Bump

---

### Post by Twitch6000 on 2009-03-07
For a simple paint program you might wanna try tuxpaint.

It is a bit more child like,but it is easy to use.

---

### Post by nathand28 on 2009-03-08
Tux and gpaint both seem to be lacking a lot of features, whereas Kolourpaint has all the features I need but doesn't work properly.
Let me put it another way. Is there a way to change Kolourpaint's default preferences to change the way it defaults to fullscreen. Where is the Kolourpaint install directory so I can edit some preference files?

---

### Post by matborda on 2009-03-17
nathand28,

I also had your same problem with KolourPaint and Firefox.

I solved following this: [http://www.tuxbay.org/component/content/190.html?task=view](http://www.tuxbay.org/component/content/190.html?task=view)

Maybe you don't know italuan :)

But it just says to write in the terminal:

first > gconftool --type=bool --set /apps/compiz/plugins/workarounds/allscreens/options/legacy_fullscreen false

and then > gconftool --type=bool --set /apps/compiz/general/screen0/options/unredirect_fullscreen_windows false

I hope it will be useful!!!

---

### Post by Timpotten on 2009-03-19
Well, It worked for me! I can now see the menu bars without having to click "settings> fullscreen" So thanks Folks! :D

---

### Post by nathand28 on 2009-03-24
> **matborda said:**
> nathand28,

I also had your same problem with KolourPaint and Firefox.

I solved following this: [http://www.tuxbay.org/component/content/190.html?task=view](http://www.tuxbay.org/component/content/190.html?task=view)

Maybe you don't know italuan :)

But it just says to write in the terminal:

first 

and then 

I hope it will be useful!!!

Thanks, it worked.
I just noticed that it was happening in Firefox too.

---

