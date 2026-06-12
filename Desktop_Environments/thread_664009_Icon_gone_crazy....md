---
title: "Icon gone crazy..."
date: 2008-01-10
forum: Desktop Environments
---

### Post by MarkoGT3 on 2008-01-10
Oh, no!

I have created a hard drive icon on my desktop by dragging it from the places menu. However, now I don't want it there any more. When I right click on it, it doesn't let me throw it away, only "unmount it" 

What should I do? I'm afraid that by unmounting it, I won't have access to my hard drive any more and that my comp will crash.:-k

Thx in advance
Marko

---

### Post by MarkoGT3 on 2008-01-10
Anyone? Please?

---

### Post by rune0077 on 2008-01-10
I'm not sure why you shouldn't just be able to move it to the trash. If it's just a link, that ought to be an option. What happens when you try it? (or is the option simply gone)

You could try and remove it through the terminal. Also, in your home-folder there's a folder called Desktop: try deleting it from there.

---

### Post by MarkoGT3 on 2008-01-10
1. Nothing happened when I dragged to trash
2. It doesn't appear in my desktop folder

:(

---

### Post by rune0077 on 2008-01-10
Okay. I think you might have added it through your gconf editor by mistake somehow. Open gconf, then browse to Apps > Nautilus > Desktop. See if Computer Icon is checked, and if it is, then uncheck it.

---

