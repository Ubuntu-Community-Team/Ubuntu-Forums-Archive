---
title: "Firefox eats 80% cpu when playing flash"
date: 2005-10-21
forum: Desktop Environments
---

### Post by shidai.liu on 2005-10-21
I don't know this is an issue of flash plugin or firefox. I've tested playing flash in firefox 1.0.7 (Breezy default) and 1.5 beta2. They both eat a lot of cpu and the fan keeps spinning.

---

### Post by chanders on 2005-10-22
I have had the same "problem"  But as long as your machine doesnt crash or you dont view two flash sites at a time! ;)

---

### Post by graigsmith on 2005-10-22
any flash animation can max out your cpu.  there is no limit to how many things you can move around with flash.  some flash artists take it too far.  i have had certain flash animations put my cpu at 100%, and i have an athlon 2800+.

---

### Post by Envel on 2005-10-22
[QUOTE=shidai.liu]I don't know this is an issue of flash plugin or firefox. I've tested playing flash in firefox 1.0.7 (Breezy default) and 1.5 beta2. They both eat a lot of cpu and the fan keeps spinning.[/QUOTE]
Add to  /etc/bash.bashrc file:
export FLASH_GTK_LIBRARY=libgtk-x11-2.0.so.0

---

### Post by shidai.liu on 2005-10-22
[QUOTE=Envel]Add to  /etc/bash.bashrc file:
export FLASH_GTK_LIBRARY=libgtk-x11-2.0.so.0[/QUOTE]

Unfortunately, this makes no difference in my labtop. I tested it using this url [[COLOR="Red"]link[/COLOR]]("http://images.linspire.com/howto/marlin/en_US/kiosk.swf").

---

### Post by magnusbb on 2005-10-22
Didn't work on my computer, either. It really eats CPU!

---

### Post by aizatto on 2005-10-22
I use the [flashblock extension]("https://addons.mozilla.org/extensions/moreinfo.php?id=433"), and just load flash applets when i want to.  :)  I know it doesn't exactly solve your problem, but you get more control.

---

