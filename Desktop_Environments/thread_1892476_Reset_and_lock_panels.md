---
title: "Reset and lock panels"
date: 2011-12-08
forum: Desktop Environments
---

### Post by littlegrn on 2011-12-08
Hello everyone.

Taking my first take to the forums so erm.... don't be too harsh on me :)

I need to know if there is a way to reset panels in Lubuntu 11.10 to their default settings and.... lock them if possible. I have a colleague that really doesn't know his way around computers and his clicking randomly by accident all the time.. can I lock the panels with a password?

---

### Post by LarsKongo on 2011-12-08
I'm not sure if lxpanel support this. It's a rather simple panel after all. Googling "LXDE kiosk mode" doesn't give me much information.

But you can try to replace lxpanel with xfce-panel. It can do kiosk mode.
See this: [http://wiki.xfce.org/howto/kiosk_mode](http://wiki.xfce.org/howto/kiosk_mode)

---

### Post by marinara on 2011-12-08
found this on the LXDE forum. 
If it doesn't work blame someone else

**EDIT you might want to use /usr/share/lxpanel/profile/Lubuntu/panels and ~/.config/lxpanel/Lubuntu/panels ? Depending on what session you are logging into

> 
            [IMG]http://forum.lxde.org/styles/prosilver/imageset/icon_post_target.gif[/IMG]by **firmit** » Sun Nov 09, 2008 9:46 am 
                            The **default** lxpanel is here: /usr/share/lxpanel/profile/**LXDE**/**panels** 

Copy this to your ~/.config/lxpanel/**LXDE**/**panels**

and you should be back to basic.
              firmit - [http://firmit.wordpress.com]("http://firmit.wordpress.com/")
                                                  **firmit**             

---

### Post by Dennis N on 2011-12-08
> **littlegrn said:**
> Hello everyone.

Taking my first take to the forums so erm.... don't be too harsh on me :)

I need to know if there is a way to reset panels in Lubuntu 11.10 to their default settings and.... lock them if possible. I have a colleague that really doesn't know his way around computers and his clicking randomly by accident all the time.. can I lock the panels with a password?

To reset panel to default (original state as when first installed):

```
lxpanelctl restart
```

As to locking the panel setup with a password, I have never seen anything about that.

---

