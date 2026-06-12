---
title: "XGL not working after updating ATI fglrx drivers"
date: 2007-09-19
forum: Desktop Effects &amp; Customization
---

### Post by styxie on 2007-09-19
Hi there, this is my first time using Ubuntu, so I might just have done something really stupid or forgotten something obvious, but please forgive me.

Anyway, I installed Ubuntu on my laptop, then installed the ATI drivers (by ticking the box in Restricted Drivers Manager) and successfully installed Compiz Fusion (using the CF_Installer v3 script). Everything was working perfectly.
Then I thought it would be cool to try to upgrade my ATI drivers, 'cause when I entered fglrxinfo in terminal, it showed I was using the 8.3 something ATI drivers, and the 8.40.4 drivers are the most recent ones for my laptop (X600). So I tried to install then using ([http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)), but whenever I log in using XGL, my screen gets all warped and I can't do anything.

Is there a way to revert back to the old drivers, because those were working just fine. Or should I update my XGL? Any help would be much appreciated.

-Styxie

---

### Post by meindian523 on 2007-09-19
Just revert to Xorg drivers using the guide given in the link you posted.

BUT,instead of doing it in terminal,press Ctrl+Alt+F1 to go to Command line after you login,ie when your screen is all warped up.Press Ctrl+Alt+F7 to get back to GUI screen and logout.If you can't logout normally,use Ctrl+Alt+F7 to logout and now login with plain Gnome.Get back our old drivers by ticking the restricted drivers in Restricted Drivers Manager.

Press Ctrl+Alt+Backspace to kill X and login now with Gnome with Xgl.Report back,please....

---

### Post by styxie on 2007-09-19
I don't know how exactly, but it working on the 8.40.4 drivers. It's allright as long as I log in straight after I boot. but if I log in with Gnome, then log out, and then log in with XGL, the **** hits the fan. However, if I log out of Gnome using CTRL+ALT+BACKSPACE, and then log in with XGL, things are fine..... I really don't know why or how this is happening, but it's fine now 'cause I can use the sexy compiz again =)

---

### Post by meindian523 on 2007-09-19
> **styxie said:**
> I don't know how exactly, but it working on the 8.40.4 drivers. It's allright as long as I log in straight after I boot. but if I log in with Gnome, then log out, and then log in with XGL, the **** hits the fan. However, if I log out of Gnome using CTRL+ALT+BACKSPACE, and then log in with XGL, things are fine..... I really don't know why or how this is happening, but it's fine now 'cause I can use the sexy compiz again =)
Does this mean that the problem is solved??Including logging out of Gnome,then logging in with Gnome with Xgl allows Compiz to work??

---

