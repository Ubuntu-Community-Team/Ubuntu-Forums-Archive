---
title: "how do I find where fonts are located?"
date: 2010-06-20
forum: Desktop Environments
---

### Post by N8N on 2010-06-20
Hi all,

been playing with my desktop and I've found that I prefer Nimbus Sans L to Arial for my default desktop font.  Was going to put it on my "shared" folder so that other people in the house (not all running Linux) could try it if they liked.  I can't find it!  It doesn't appear to be in usr/share/fonts as you would expect.  (I did find the other font that I wanted to share, Inconsolata...)  however Nimbus Sans L does appear in the font selection menus for gnome, Oo.o, Firefox, Thunderbird, etc...  is there a way to find where the .ttf is located so that I can share it?

It does appear to be properly installed, as it is distinct from the other Helvetica-like fonts that I have...

thanks

Nate

---

### Post by ajgreeny on 2010-06-20
Try ```
locate -i .ttf | grep -i Nimbus
```.  As long as you know the file name of the font it will find it for you.

The ** -i** part makes the commands case insensitive.

---

### Post by N8N on 2010-06-21
I'm mightily confused... command does not return anything.  It's not the command that's incorrect, because it works with 'inconsolata' just fine.

I'm not 100% certain that it is a .ttf font, but I assume that it is.

nate

---

