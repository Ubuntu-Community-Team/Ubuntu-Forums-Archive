---
title: "beryl or compiz, xgl or aigxl? (I want to run AWN)"
date: 2007-05-13
forum: Desktop Effects &amp; Customization
---

### Post by thelost on 2007-05-13
I realize that there is a post here:
[http://ubuntuforums.org/showthread.php?p=2307772](http://ubuntuforums.org/showthread.php?p=2307772)

On installing AWN. However I am interested in finding out which compositor, Beryl or Compiz is better to install. I read that Beryl is being merged back into Compiz, and I was also wondering if Compiz is more stable?

Also, I haven't chosen XGL or AIGXL yet, which is simpler to install? As I remember it XGL is much simpler, is this still the case?

Also, unrelated question but I want to replace my ubuntu start menu's icon with an apple.png. I realize that I need replace the distributor logo or 'start-here.png' however having changed them in the tango/human/hicolor folders the logo hasn't changed. Any ideas?

---

### Post by jocko on 2007-05-13
The choice between aiglx and xgl depends on which graphics card and which drivers you use.
Aiglx is already included in ubuntus xorg, so if you are lucky and have a card/driver combination that supports it you don't need to do anything.
If you use an integrated intel card or an ati card using the open source (radeon) drivers you should go for aiglx (i.e you don't need to do anything. just install compiz or beryl).
The newer versions of nvidia's propretary drivers have their own built in functions that doesn't need aiglx or xgl.
If you have an Ati card and use ati's proprietary drivers you have to install xgl.

---

### Post by thelost on 2007-05-13
i'm using the nvidia drivers, version 1.0-9755.

also, anyone know about beryl vs compiz?

& finally, a question I forgot to ask before; Is AWN worth the hastle or is there another dock for gnome you think is better? Is AWN reasonably stable? I realize it's beta, but that doesn't always mean it's a crash fest!

---

### Post by mrojas73 on 2007-05-13
I like them both, I got compiz on my desktop and Beryl on my laptop thought compiz is easier to set up I think.

---

