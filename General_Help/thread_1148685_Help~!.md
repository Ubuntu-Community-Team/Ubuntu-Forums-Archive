---
title: "Help~!"
date: 2009-05-04
forum: General Help
---

### Post by Sevag on 2009-05-04
Hey
im following this guide to give my desktop a macintosh os look

[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)

i made it to the fonts part i installed the fonts but cant proceed in anything he's saying copy the osx fonts to the fonts folder
but i cant find the osx fonts nor the fonts folder
and if i put the codes below it in the terminal it gives me an error after the second code 

sevag@sevag-laptop:/usr/share/fonts$ cd /usr/share/fonts
sevag@sevag-laptop:/usr/share/fonts$ sudo tar xvzf /home/username/Mac_files/Mac4Lin_v0.4/Fonts/OSX_Fonts.tar.gz
tar: /home/username/Mac_files/Mac4Lin_v0.4/Fonts/OSX_Fonts.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
sevag@sevag-laptop:/usr/share/fonts$ 

Any help will be appreciated. :)

---

### Post by Sevag on 2009-05-04
Oh yes and i use Ubuntu 9.04

---

### Post by john183 on 2009-05-04
Just a quick note based on the output you posted.
> sevag@sevag-laptop:/usr/share/fonts$ sudo tar xvzf /home/[COLOR="Red"]username[/COLOR]/Mac_files/Mac4Lin_v0.4/Fonts/OSX_Fonts.tar.gz
tar: /home/username/Mac_files/Mac4Lin_v0.4/Fonts/OSX_Fonts.tar.gz: Cannot open: No such file or directory

you should change "username" to your actual username.

---

### Post by Sevag on 2009-05-04
Thx
And sorry for the noobish question  :\

---

### Post by Sevag on 2009-05-04
Done it worked!

---

### Post by john183 on 2009-05-04
No problem. Just remember to check for things like that when you are copying code from webpages or other documents. And make sure that you have some idea of what the code is supposed to do before you run it. Some people are not exactly nice and will post code that will screw up your computer.

---

