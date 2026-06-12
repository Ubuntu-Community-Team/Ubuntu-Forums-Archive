---
title: "themes problem"
date: 2006-12-21
forum: Desktop Environments
---

### Post by ad4m_net on 2006-12-21
I am wandering how you can change the theme for the screen after you logon but before the window manager loads. In my case I am using gnome and a screen loads up after I login and shows it loading the window manager. I was wondering how you go about changing this screen with a theme. I looked around on some of the theme sites, but didn't really find what I was looking for. Hope someone can point me in the right direction. Thanks

---------------
Adam Whiles
[http://www.phpshack.net](http://www.phpshack.net)

---

### Post by iamhugeinjapan on 2006-12-21
See #6 in this thread:

[http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

---

### Post by ad4m_net on 2006-12-21
Ok thanks, I got that changed, but now how do I change the background color on that? I have a dark/black theme for my whole system, and that default ubuntu color does look right at all. Is there a setting I can change or something. Thanks for your help

---

### Post by iamhugeinjapan on 2006-12-21
I've wondered that myself. I tried changing the solid colour displayed when there is no desktop picture set but that didn't help. I don't usually see it because it doesn't display when running an XGL session.

It's probably able to be changed in the gconf-editor program.

---

### Post by mcduck on 2006-12-22
you only need to change the background color for the wallpaper you are using (not the (no-wallpaper one!).

But that doesn't work with XGL.

---

### Post by ad4m_net on 2006-12-22
well, i figured it out a little while ago. I don't know why I didn't see that before lol. Just run "sudo gdmsetup" and there is the color setting right in my face. Thanks for the help!

---

