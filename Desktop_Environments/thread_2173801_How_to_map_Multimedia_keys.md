---
title: "How to map Multimedia keys"
date: 2013-09-11
forum: Desktop Environments
---

### Post by gspe on 2013-09-11
Hi,
I was looking at this mechanical keyboard [http://codekeyboards.com/](http://codekeyboards.com/) and i liked the idea of multimedia keys position.
[IMG]http://codekeyboards.com/img/code-mediakeys.jpg[/IMG]


What I was tying to do was to remap my menu key to Fn key and use the combination of Fn- keys to map multimedia function.
I looked various guide  but I haven´t found what I´m looking for.
I know that i have to use XKBOPTIONS but i can´t find the code for the Fn key.

Can someone help me?

---

### Post by tgalati4 on 2013-09-11
If *xev* does not reveal the keycodes then you have to set a keycode using one of several techniques.  [http://ubuntuforums.org/showthread.php?t=921870&highlight=keycode](http://ubuntuforums.org/showthread.php?t=921870&highlight=keycode)

Take careful notes and post what works and what doesn't.  You may need to email the manufacturer for the scan codes for certain keys to be able to set the keycode.

Alternatively, go through the various keyboard models in keyboard settings and find one that gives you the most functionality.  I'm guessing there is a Windows driver that is used to get the Fn-multimedia keys to work, because they are not part of a standard or traditional layout.

---

### Post by gspe on 2013-09-11
Thank for your reply.

After a day of research I've decided that would be much simple to map the multimedia key with right control + page down / page up  etc...

---

