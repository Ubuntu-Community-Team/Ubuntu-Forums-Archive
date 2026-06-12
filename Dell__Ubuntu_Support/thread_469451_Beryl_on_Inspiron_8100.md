---
title: "Beryl on Inspiron 8100"
date: 2007-06-09
forum: Dell  Ubuntu Support
---

### Post by Atzu on 2007-06-09
I'm sorry im new to ubuntu, I'm trying to run beryl on this computer but all i can get is a black screen. :(

[IMG]http://i35.photobucket.com/albums/d184/Atsure/Screenshot.png[/IMG]

---

### Post by kamaboko on 2007-06-09
"It's more than black"
                            - Nigel Tufnel

---

### Post by Atzu on 2007-06-09
Well it's good the screen wasn't blue.

---

### Post by jiminycricket on 2007-06-10
What kind of video card and drivers?

If it's an old card, Try:

> 
You can create /etc/drirc file with the following contents:
<option name="allow_large_textures" value="2" />

However, it's most probable your graphics card does not enough video RAM to handle the multiple large textures anyway.

If it's proprietary nVidia, I believe that's a famous bug of theirs.

---

### Post by Atzu on 2007-06-10
Now beryl works, I downloaded "beryl settings manager (simple)", but i cant maximize windows or they will become a black screen. Thanks a lot for helping.

---

### Post by jiminycricket on 2007-06-10
There's some info here on the bug in the nVidia proprietary driver:

[http://www.nvnews.net/vbulletin/showthread.php?t=92622](http://www.nvnews.net/vbulletin/showthread.php?t=92622)

Also, if you have time, there's a link in my sig to help an open source/free software project called 'Nouveau' reverse engineer the nvidia drivers so bugs like this can be fixed by anyone, instead of relying on nVidia (who haven't fixed it in a LONG time).  All you have to do is run a program and email the results to the developers.

---

