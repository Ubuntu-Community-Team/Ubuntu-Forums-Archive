---
title: "Top panel disapears from time to time"
date: 2012-02-02
forum: Desktop Environments
---

### Post by thepanda0 on 2012-02-02
This is one of the stranger problems I have experienced, from time to time my top panel bar will disappear. This usually happens when I close a window. I will still be able to click on it, but it isn't visible. Usually when this happens my temporary fix for it is to click the main menu click shut down, at which point nothing happens, then do this again, at which point the shut down/restart/ suspend prompt comes up and restores my panel to normal. This solution will only last for a few minutes though. I'm using the gnome panel 2.30.2 for Lucid Lynx. Any advice would be greatly appreciated thank you.

---

### Post by thepanda0 on 2012-02-05
Anyone? :(

---

### Post by josephmills on 2012-02-05
this might work for yah next time this happens open a terminal (ctrl+alt+t) then  enter ```
gconftool --recursive-unset /apps/panel && killall gnome-panel 
```
this will reset the panel to default., Hope that this helps

---

### Post by thepanda0 on 2012-02-06
This didn't work. I'm still getting the same problem.

---

### Post by finny388 on 2012-02-07
sorry, I don't know - but here's a bump for your strange problem.

---

### Post by hansdown on 2012-02-07
Hi, thepanda0.

I still have a lucid install.

Still love it, but the top bar bugs still persist.

This is probably the best advise.

[http://shibuvarkala.blogspot.com/2009/09/howto-recover-gnome-panel-disappeared.html](http://shibuvarkala.blogspot.com/2009/09/howto-recover-gnome-panel-disappeared.html)

---

### Post by thepanda0 on 2012-02-10
Hansdown, It seems like this worked. Thank you! :o

---

### Post by hansdown on 2012-02-10
Glad you fixed it, thepanda0,  :D

---

