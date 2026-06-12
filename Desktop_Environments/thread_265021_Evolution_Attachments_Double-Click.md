---
title: "Evolution Attachments Double-Click"
date: 2006-09-25
forum: Desktop Environments
---

### Post by tebbendj on 2006-09-25
I have searched these forums and Google with no luck on my problem.  When I double click an attachment in Evolution I get an error that the file cannot be found.  It is trying to load it from a location that seems incorrect.  (i.e. file:///home/dan/file:/home/dan/.evolution...)  I have looked for where the setting are defining this path, but to no avail.  Something is causing it to add "file:/home/dan" twice.

If Iright click the attachment and use the "open with" then all is fine.  I can also save the file to my desktop and then open it fine by double-clicking.  

Can someone point me to where to define the path to the Evolution cache so double clicking will work.

Thanks.

---

### Post by tebbendj on 2006-09-26
I wrote the original post.  I have narrowed down the problem a bit.  The problem was with .wav and .wmv files (at least).  PDF files work correctly.  I have changed the default program for .wav from Totem to GXine.  It now works correctly.  However, when trying XMMS the .wav file still would not play.  At least I have it working well enough using GXine, but I would still like to know why the link to the temporary file doesn't pass correctly from Evolution to Totem.  Using "open with" works with both Totem and XMMS, so I know the file is supported.

---

