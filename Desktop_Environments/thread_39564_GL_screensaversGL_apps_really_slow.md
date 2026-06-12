---
title: "GL screensavers/GL apps really slow"
date: 2005-06-05
forum: Desktop Environments
---

### Post by Heretic09 on 2005-06-05
Using any GL screensaver causes my system to slow to a crawl. I have accelaration enabled in the xorg.conf. Even if I exit out of the screensaver everything is really really slow until I quit the control center and then everything goes back to normal.

glxgears spin really fast for 8 seconds and then starts to crawl and causes my whole system to crawl until I close the gears window.

I have a p4 3.2 ghz with a gig of ram and nvidia 5200 so its not my specs. How do I set it up so that gl applications run normally or take advantage of 3d acceleration?

I have noticed that if I do

glxinfo |grep rendering

I get 
direct rendering: no

i'm assuming thats the culprit, i'm wondering how to get that to say yes, dri is set to 666 permissions and I have load glx and load dri in the xorg.conf

---

### Post by Heretic09 on 2005-06-05
glxinfo shows that the server glx version is 1.2 and the client glx version is 1.4, i'm assuming thats the problem, anyone know how to make sure both match?

---

### Post by Heretic09 on 2005-06-05
Well it seems that you need updated linuxl-restricted-modules for 2.6.11 for the glx server to go up to 1.4. Ofcourse there is no such updated package, only one is up to 2.6.10. The alternative is to install the official nvidia drivers which would be fine except that installing it gives you a black screen on startup with no error messages. 

I'm really trying to like kubuntu but the more I dig deeper the more its seems like a half assed distro in comparison to the Suse, slackware even gentoo.

---

