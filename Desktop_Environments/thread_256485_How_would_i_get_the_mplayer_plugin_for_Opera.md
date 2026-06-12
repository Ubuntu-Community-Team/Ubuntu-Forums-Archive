---
title: "How would i get the mplayer plugin for Opera?"
date: 2006-09-13
forum: Desktop Environments
---

### Post by someguyouknow on 2006-09-13
can someone point me in the right direction?

thanks in advance...

---

### Post by xyz on 2006-09-13
I found a couple of links...hopefully...
[http://ubuntuforums.org/showthread.php?t=74667](http://ubuntuforums.org/showthread.php?t=74667)
[http://www.ubuntuforums.org/archive/index.php/t-76236.html](http://www.ubuntuforums.org/archive/index.php/t-76236.html)

---

### Post by jazzgossen on 2006-09-13
I did this:

Install mozilla-mplayer from the repositories.
cp /usr/lib/mozilla/plugins/mplayerplug-in*.{so,xpt} /usr/lib/opera/plugins
ln -s /usr/lib/mozilla/libxpcom.so /usr/lib

---

### Post by someguyouknow on 2006-09-13
I tried both and it didnt work...
thanks for the suggestions though...

---

### Post by someguyouknow on 2006-09-13
for some strange reason, it doesnt seem to recongnize the mplayer plugin ins but i got the kaffeine plugin to work... its external but its not bad.

---

### Post by rebegin on 2006-09-17
try this on if you want video in the browser:
[http://ubuntuforums.org/showthread.php?t=179694&highlight=file+directory+error%3A+X11%2FIntrinsic.h%3A](http://ubuntuforums.org/showthread.php?t=179694&highlight=file+directory+error%3A+X11%2FIntrinsic.h%3A)

---

### Post by someguyouknow on 2006-09-17
when you did this, did you just use --enable-x or did you add that on to the gecko-sdk?

---

### Post by someguyouknow on 2006-09-17
nvm... i dont think i can get this to work. i might have to stick to kaffeine...

edit: i got mplayer to work but i am not sure if i want to keep it. there is no controls for it like on firefox...

---

