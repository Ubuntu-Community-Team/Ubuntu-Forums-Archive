---
title: "Flock+ Flash problem!"
date: 2008-12-15
forum: General Help
---

### Post by iampriteshdesai on 2008-12-15
I have installed Flock by following the instructions given here:
[http://helpforlinux.blogspot.com](http://helpforlinux.blogspot.com)
Now I have flash up and running, but it didn't work in Flock and it kept on bugging me for installing it. I installed it again, did a restart but still it says install flash.
What to do?
Why doesn't it accept flsh like Firefox does?

---

### Post by nikgare on 2008-12-15
You need to copy libflashplayer.so to ~/.flock/plugins

---

### Post by iampriteshdesai on 2008-12-15
Where can I find this file?
libflashplayer.so

---

### Post by nikgare on 2008-12-15
~/.mozilla/plugins/libflashplayer.so

Hope this helps

---

### Post by iampriteshdesai on 2008-12-15
I searched for the folder .mozilla/plugin it wasn't there. There was a folder called extensions. Even in flock there was a folder called browser.
Where is the folder plugin?

---

### Post by nikgare on 2008-12-15
maybe it's in a different place on your system.
Try doing **locate libflashplayer.so** and seeing what's there.  You'll probably find most are just links to the real file.

---

### Post by iampriteshdesai on 2008-12-16
yeah, I found it and pasted it into flock folder, it was in usr/flock/plugins
however now I do not get any flash warnings but I cannot see any flash, tried youtube.
I read somewhere that flashplayer.xpt was also required, where do I get it? I tried the .deb files but couldn't see it!
Plz help. and usr/mozilla/firefox don't have the libflashplayer.so

---

### Post by iampriteshdesai on 2008-12-16
Here is the link to that article, read the 5th comment: [http://tuxicity.wordpress.com/2007/05/14/flock-the-social-web-browser-on-ubuntu-feisty-fawn-no-working-flash/](http://tuxicity.wordpress.com/2007/05/14/flock-the-social-web-browser-on-ubuntu-feisty-fawn-no-working-flash/)

---

### Post by iampriteshdesai on 2008-12-16
Solved, this time I copied the proper libflash.so from the firefox setup and now it works, thanks!

---

