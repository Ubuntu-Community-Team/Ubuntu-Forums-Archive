---
title: "How to move minimize, maximize and close to the right?"
date: 2012-06-01
forum: Desktop Environments
---

### Post by ubto66 on 2012-06-01
ubuntu 12.04lts.
how to move icons minimize, maximize and close to the right?
on ubuntu 10.04lts it can be done like this [http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/](http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/)
Thanks.

---

### Post by ksprasad on 2012-06-01
Hi,
 
I didn't try this, but quick googling gave this:
 
[http://alexsleat.co.uk/2012/04/11/ubuntu-12-04-moving-the-windows-buttons-back-to-the-right/](http://alexsleat.co.uk/2012/04/11/ubuntu-12-04-moving-the-windows-buttons-back-to-the-right/)
 
Regards,
ksprasad

---

### Post by kansasnoob on 2012-06-01
Depending on what desktop environment you're using you may find step #6 here helpful:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by ubto66 on 2012-06-01
> **ksprasad said:**
> Hi,
 
I didn't try this, but quick googling gave this:
 
[http://alexsleat.co.uk/2012/04/11/ubuntu-12-04-moving-the-windows-buttons-back-to-the-right/](http://alexsleat.co.uk/2012/04/11/ubuntu-12-04-moving-the-windows-buttons-back-to-the-right/)
 
Regards,
ksprasad
Thanks for answering I would prefer a solution that is using the 
gconf-editor.

---

### Post by DMGrier on 2012-06-01
So lets say I do this cause I do prefer them on the right, but in Unity does that mean when I maximize them that it will still go on the right near the chat icon? Has anyone done this?

---

### Post by satish_j on 2012-06-02
> **DMGrier said:**
> So lets say I do this cause I do prefer them on the right, but in Unity does that mean when I maximize them that it will still go on the right near the chat icon? Has anyone done this?

One can make them go to the right after changing some settings in gconf-editor,but that will be applicable only while the app window is not maximized.
Maximizing the application window will shift all 3 again to unity's top panel on the left.This is the default behaviour in unity and thus far,there is no work-around for it.

---

### Post by Jaskaran498 on 2012-06-02
Try this in terminal-

```
gconftool-s/
apps/
met>gconftool-
s/apps/
met>gconftool-
s/apps/metacity/
general/
button_layout-t
string
menu:minimize,maximize,close
```

this makes buttons move to right side in correct order.
hope this helps. :)
good luck.

---

### Post by ubto66 on 2012-06-09
[SIZE=2]Thank you for the answers. I went with [/SIZE]gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
 [SIZE=2]And it worked.[/SIZE]

---

