---
title: "broken compiz mipmaps after nvidia -&gt; ati"
date: 2008-03-03
forum: Desktop Effects &amp; Customization
---

### Post by stinkinrich88 on 2008-03-03
Hello,

I've finally got my ATI card working (thanks Envy!). Only two problems: 

1. The mipmaps in compiz are broken now. This includes in expo and window previews. I have to disable them and it looks pixelated without them. 

2. Flickering video (to do with opengl I believe) but I've found another thread that is working on this

3. no more boot screen (you know, the orange worm), don't really care about this though

So if anyone could help me out (mainly with number 1) I'd really appreciate it! thanks!

---

### Post by Melcar on 2008-03-03
What card is it?  My R6XX cards (the HD models) cannot render mipmaps at all (they just render black squares).  The flickering is a persistent problem, and unless you are running an nvidia card with their binary blobs, you will have to deal with this issue (quick fix is to use X to render instead of OGL or Xv).

---

### Post by stinkinrich88 on 2008-03-03
hi, it's the AIT Radeon Sapphire HD 2400 Pro card. 

I have sorted the flickering video out for VLC (by using x instead) but totem etc are still broken.

---

### Post by Melcar on 2008-03-03
If you're using gstreamer, you need to change the rendering method in the Multimedia Systems Selector.  It doesn't show on the default GNOME menu layout, so you're going to have to open Alacarte (the GNOME menu editor) and enable it; it should be under System>Preferences.
As for the mipmaps, I have both a HD2900XT and a HD3850, and they both fail to render mipmaps, regardless of what fglrx version I use.

---

### Post by stinkinrich88 on 2008-03-08
ahh fair enough, thanks for your help, I'll just put up with grainy quality. 

as for problems 2 & 3, they were both solved with a clean install of hardy alpha 6

---

