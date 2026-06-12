---
title: "[SOLVED] Rectangles instead of symbols.. Looks like alpha channel in cairo is broken."
date: 2008-05-13
forum: Desktop Environments
---

### Post by Noisedsn on 2008-05-13
In some programs font rendering don't work correctly for me.

For example, in firefox 3 beta when I drag some selected text it looks like small black rectangles instead of font characters. But when I launched the Hardy Heron Live CD I didn't see this problem.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=69903&stc=1&d=1210698439[/IMG]

In Elisa Media Center text strings are completely unreadable because of white rectangles at the same places where characters must be placed.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=69904&stc=1&d=1210698439[/IMG]

It is not character table or locale problem, It looks like rectangular place where symbols are placed is filled with black or white.

Maybe I broke something trying to tune the font rendering. But it was about half of year ago and I can't remember what I was doing exactly...

Do someone know where the problem is? Or I need to reinstall the system completely?

---

### Post by Noisedsn on 2008-05-14
I attached the screenshots, so you can see the problem.

---

### Post by lykwydchykyn on 2008-09-13
Hello,
I've been having this problem on two different hardy machines; I see this thread is marked solved, but I don't see the solution.  What did you do to fix this?

---

### Post by Zephon_Soul on 2008-09-14
Hello, I had this problem too. I suggest you to try a different set of fonts. This is what happened to me:
I was having this issue both on the window thumbnails with the compiz plugin (the names of the windows appeared as black squares) and within OO.org with Impress (animated text appeared inside black squares during animation). I was using Nimbus Sans fonts, so I tried to switch back to defalut Sans: the issue vanished. Even more surprising, I set back to Nimbus Sans all the fonts, and it's still working. Unfortunately I see that the window labels in compiz thumbs are written with Sans, so I suspect after X gets restarted the same problem may appear again. I still have to try it, but if that's the case, then this may be an issue with some font's rendering properties.

Hope this helped! ;)

---

### Post by lykwydchykyn on 2008-09-15
Thanks for the reply.  If I change the font and restart X, it works once, then starts again.  It's most notable when xfrun4 is doing autocomplete.  It will work fine once, but on subsequent runs the completion suggestions are just black boxes.  It's also done this when printing, which was pretty irritating (fonts looked fine on the screen, but turned into boxes when printing).

I've scoured for this problem with google, but only a few seem to have it.  Maybe I don't know what to search for.

---

### Post by Zephon_Soul on 2008-09-16
Well if it isn't strange...
On my desktop I had this issue with compiz thumbs and OpenOffice (probably also with evince on the text "loading document") but no problems with Elisa... now I've just noted that my laptop doesn't have OO or compiz issues but it has the Elisa ones (and nothing seems to fix it). :confused:
Are you having issues with Elisa, OO.org, compiz or another app? On my desk the solution I wrote earlier worked fine even after several reboots.

---

### Post by lykwydchykyn on 2008-09-20
I use XFCE with compiz on my laptop, XFCE without compiz on the desktop.  Both experience this problem, not with standard text but with things like:

1. If I'm typing into xfrun, the autocomplete suggestions that show up below where I'm typing are like this.
2. If I'm dragging text out of an application like firefox, the dragged text is like this.
3. Sometimes if I print, the printed page (including the preview) is like this.

I notice under close inspection that what's happening is that the background around the affected text is black.  If the text in question happens to be red or white, I can see the letters on the rectangles.  Just not sure why they are getting this black background.  

I've tried different fonts, and certainly my laptop gets restarted all the time, but it doesn't go away.

---

