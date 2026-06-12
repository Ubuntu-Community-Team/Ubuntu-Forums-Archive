---
title: "xgl/compiz wobbly funny business"
date: 2006-06-11
forum: Desktop Environments
---

### Post by snoops on 2006-06-11
I've been messing about with the settings for compiz, in particular the plugin wobbly. 

I've got it so if I move a window with sufficient velocity then release my hold on it, that it'll keep sliding on the screen.. if you throw them hard enough you throw them off the screen - absolutely cool feature. I've wanted to throw away my windows for years (pun intended). I've also got it so if I throw them under a certain velocity that they will snap to the window they're moving towards. With a bit of practice I think I'll get it down to an art. 

The strange behaviour I'm finding though is related to while the window is wobblying after release.. when you move it slowly the wobble isn't much, so when you release the cursor half a second later, it 'sets' itself back on the desktop again. However if you move the window at a normal speed (for what I consider normal), the wobble will be a bit greater, so then if you click something within that window while it's still wobblying your mouse event will click the window behind that, if any..or it'll just click the desktop behind it. 

This seems very strange which leads me to believe when a window is wobblying, the x, y defining its position isn't set until the wobble reaches under a certain amount - where do I set that amount?

Has anyone else noticed this when you reduce the friction a tad (which is what I had to do to be able to throw windows) that you end up clicking through the window while it's finishing its wobble. You'll probably notice it more if you look at text.. While it's wobbling the text is unfocused, but when it finishes, you'll see a little 'snap' almost.. Where everything comes into focus again. 

If anyone can help me reduce the wobble while maintaining my throwing window abilities or help me fix this clicking through the window before it finishes it's wobble, that would be fantastic.

Thanks

---

### Post by manicka on 2006-06-11
I can't stand the wobble. Makes me feel motion sick with the way it handles menus. [IMG]http://smileys.on-my-web.com/repository/Others/sick-298.gif[/IMG]

It's the first plugin I disable

---

### Post by chavo on 2006-06-11
[QUOTE=manicka]I can't stand the wobble. Makes me feel motion sick with the way it handles menus. [IMG]http://smileys.on-my-web.com/repository/Others/sick-298.gif[/IMG]

It's the first plugin I disable[/QUOTE]
I didn't like the wobble at first either, but you can disable it for menus. Just disable the wobble effect on unknown windows and your menus won't wobble.

---

### Post by manicka on 2006-06-11
[QUOTE=chavo]I didn't like the wobble at first either, but you can disable it for menus. Just disable the wobble effect on unknown windows and your menus won't wobble.[/QUOTE]

Ah, didn't know that. I'll give it a go...thanks :D

---

### Post by snoops on 2006-06-11
So..Nobody has any idea about this click through the wobbling window bug or how to reduce the wobble so that doesn't happen?

:(

---

