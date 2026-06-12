---
title: "Wbar issues, &quot;Couldn't load font?&quot;"
date: 2009-06-30
forum: Desktop Environments
---

### Post by thedinga on 2009-06-30
I've tried installing wbar and to my knowledge its installed but this is where i get stuck when i call it in the terminal...

Using /usr/share/wbar/dot.wbar config file.
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_free_image();

    With the parameter:

    image

    being NULL. Please fix your program.
/usr/share/wbar/iconpack/wbar.osx/font/12 -> Couldn't load font.

I've searched and posted in a few forums, the only thing i've gathered is that one of the ttf (i think font.ttf) isn't linked to comic.ttf and might be solved with a reinstall.  I'm really new to linux and the fact that i've gotten this far kinda surprises me but if anyone has any pointers and might be able to walk me through step by step, I'd really appreciate it.

---

### Post by fluxbuntu on 2009-09-04
Everything wbar is installed at /usr/share/wbar. You should see font.ttf there. You can download any ttf and name it font.ttf and replace it if it's messed up for any reason. Assuming that you, like me, would be changing your wbar icons and setup often, you may wish to change permissions on that diredtory via

sudo chmod 777 --recursive /usr/share/wbar

Did you install wbar with a .deb file or compile? I had issues with compiling that resolved by installing the .deb

---

### Post by ldp on 2009-11-06
In Karmic the *font* seems to be a link in /usr/share/wbar/iconpack/wbar.osx/
I tried creating a new link(s) to font(s) however each time it failed.

What worked for me.

I chose a font /usr/share/fonts/truetype/freefont/FreeSansBold.ttf
Then copied the .ttf to /usr/share/wbar/ and renamed it font.ttf

It seems one may choose any truetype font.

---

