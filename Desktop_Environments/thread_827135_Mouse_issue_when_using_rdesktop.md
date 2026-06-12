---
title: "Mouse issue when using rdesktop"
date: 2008-06-12
forum: Desktop Environments
---

### Post by toolzen on 2008-06-12
Hi! I recently set up and old computer to boot up to the gdm, and when the user logs in their blackbox session goes directly into a fullscreen rdesktop to our Windows 2003 terminal server. Everything works great, except every now and again (but not all the time) when she is working in a document (in ms word) and she clicks in the document to move the cursor (not the mouse cursor, but the blinking cursor in MS Word that shows where you will type if you start typing), it will highlight everything from where the cursor originally was to where she clicks. When this starts happening she also looses the functionality of her scroll wheel. She is using a Microsoft "IntelliMouse-" a misnomer if ever there was one. It is an optical mouse rather than one with ball.

I have already tried all the obvious things: changed mouse, checked xorg.conf, read over the forum for similar problems, etc. Also, I know it's not a problem on the Windows Terminal Server side because everything worked just fine for the user before I switched her to this "dummy" terminal.

It looks almost like what would happen if you held down the shift key and clicked, so I am going to try replacing her keyboard though she is using one of those "lifetime" keyboards and those things are hard to mess up. I would also note that she is using a keyboard ps/2 chord extender, so she doesn't have to type on the very edge of her spacious desk. How likely would it be for that to be the culprit?

I guess what I'm ~hoping~ is that somebody has had this exact same problem and might know how to fix it. Any helpful ideas would be greatly appreciated.

Also, if I do get her a new keyboard and/or mouse, what is the easiest way to reconfigure that? Just edit xorg.conf? Or run some  built-in script perhaps?

---

### Post by toolzen on 2008-06-26
Bump.

This is still an intermittent problem. Anyone has any suggestions?

---

