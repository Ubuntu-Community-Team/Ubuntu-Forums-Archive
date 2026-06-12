---
title: "Nautilus File Manager looks strange in Lucid"
date: 2010-05-07
forum: Desktop Environments
---

### Post by Esau on 2010-05-07
Hello.

I need some help restoring my Nautilus File Manager back to its original  state. I tried installing Elementary Nautilus but for some reason it  was not working for me, so I uninstalled it but have been having an  issue with Nautilus looking like its former self. Now Nautilus doesn't  display the "tree" on the left, there are no back/forward icons, and  generally looking strange.

Here's a picture to showcase my issue:



[http://lh3.ggpht.com/_YhNnPAf5q0U/S-RAS7ETVqI/AAAAAAAABeQ/DKB4bf3n2bI/s800/Screenshot.png](http://lh3.ggpht.com/_YhNnPAf5q0U/S-RAS7ETVqI/AAAAAAAABeQ/DKB4bf3n2bI/s800/Screenshot.png)



[IMG]http://picasaweb.google.com/lh/photo/LW1ZI5Z55L5683SXNLx7mw?feat=directlink[/IMG]

I would love to use Elementary Nautilus but can not get it as my default  file manager. Since I can't do that I just want Nautilus (the one that  comes shipped with Ubuntu) to look and act like it's supposed to.

Any suggestions/advice would be appreciated.

Thanks

---

### Post by ammonkey on 2010-05-07
well u got the stock nautilus actually. You are just in spatial mode. There's a gconf key to return to the more conventional browser mode. open gconf-editor and change the following key: apps/nautilus/preferences/always_use_browser.

About your nautilus-elementary install problem, i think you just forget to restart nautilus (nautilus -q) or close/open your session.

---

### Post by Esau on 2010-05-07
> **Esau said:**
> Hello.

I need some help restoring my Nautilus File Manager back to its original  state. I tried installing Elementary Nautilus but for some reason it  was not working for me, so I uninstalled it but have been having an  issue with Nautilus looking like its former self. Now Nautilus doesn't  display the "tree" on the left, there are no back/forward icons, and  generally looking strange.

Here's a picture to showcase my issue:



[http://lh3.ggpht.com/_YhNnPAf5q0U/S-RAS7ETVqI/AAAAAAAABeQ/DKB4bf3n2bI/s800/Screenshot.png](http://lh3.ggpht.com/_YhNnPAf5q0U/S-RAS7ETVqI/AAAAAAAABeQ/DKB4bf3n2bI/s800/Screenshot.png)



[IMG]http://picasaweb.google.com/lh/photo/LW1ZI5Z55L5683SXNLx7mw?feat=directlink[/IMG]

I would love to use Elementary Nautilus but can not get it as my default  file manager. Since I can't do that I just want Nautilus (the one that  comes shipped with Ubuntu) to look and act like it's supposed to.

Any suggestions/advice would be appreciated.

Thanks

> **ammonkey said:**
> well u got the stock nautilus actually. You are just in spatial mode. There's a gconf key to return to the more conventional browser mode. open gconf-editor and change the following key: apps/nautilus/preferences/always_use_browser.

About your nautilus-elementary install problem, i think you just forget to restart nautilus (nautilus -q) or close/open your session.

Thank you VERY much ammonkey. I've been struggling with that for a while now. Not sure how it even got changed to spatial mode. This upgrade was not as smooth as the last few I've encountered.

Thanks again for your help.

You :guitar:!

---

