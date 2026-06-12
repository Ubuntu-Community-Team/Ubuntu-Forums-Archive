---
title: "Beryl window thumbnails?"
date: 2007-01-30
forum: Desktop Environments
---

### Post by Russty of Oz on 2007-01-30
Hi,

I was wondering if anyone knows how to get minimized windows thumbnails to work in Beryl?  I have checked and in the Beryl Settings under the General tab it is showing as enabled, but I just don't get them.  Is there something else I have to do?

Russty

---

### Post by lawina on 2007-01-30
Same here. It stopped working for me in version 0.2 beta. Beryl with Emerald works fine though.

---

### Post by mayonaise15 on 2007-01-30
Run this command:
```
sudo apt-get install beryl-plugins-extra
```
Then go to the Extras tab to make sure Window Thumbnails has a check mark next to it.

---

### Post by rudder on 2007-01-30
I had the same issue and your suggestion to install the extras worked like a charm... however, now whenever a window is minimized it's thumbnail is upside down.  The thumbnail's window border is fine with all the buttons in the proper places but the stuff inside the window is flipped vertically.  Here are some pictures... That's not normal, is it?

Also, the thumbnails did something funky in the screenshots but look normal in use.  I guess I should start using the Beryl screenshot plugin instead of the screenshot button...

Maximized:
[http://i53.photobucket.com/albums/g56/badbox29/maximized.png](http://i53.photobucket.com/albums/g56/badbox29/maximized.png)

Minimized:
[http://i53.photobucket.com/albums/g56/badbox29/minimized.png](http://i53.photobucket.com/albums/g56/badbox29/minimized.png)

---

### Post by mayonaise15 on 2007-01-30
Now that is strange...have you tried forcing a restart of the window manager by either logging out/in or clicking on the Beryl-Manager icon and clicking Reload Window Manager?

---

### Post by Russty of Oz on 2007-01-30
I did that and it works fine.  And my thumbnails ARE up the right way!

Thanks :D

---

### Post by rudder on 2007-01-31
I sure did... I even went as far as to uninstall all the Beryl stuff and reinstall it.  I have another machine at my work that I keep for tooling around with and it is exactly the same way.  The weirdest thing to me is how it only is a problem for minimized windows...

---

