---
title: "Virtualbox- USB/ Hard drives"
date: 2009-04-27
forum: General Help
---

### Post by Godgothic182 on 2009-04-27
I've searched in many sites what can I do for activate the usb ports in the virtualbox. I've installed windows xp with virtualbox and I want to be able to use the usb...........I need the usb for connecting to internet (wireless),for example

Another thing, I would like to be able to enter on the other hard drives of my computer (two, one with ubuntu, the other with win media center edition), is it possible? when I open MIPC in virtualbox with windows xp professional, only apears hard drive C, that's the image created with virtualbox for installing the operating system...........

Thanks for the help







P.D. I believe that is posted on the corrrect site......there isn't a forum for aplications/programs

---

### Post by avri210984 on 2009-04-27
So far the only way I was able to use the USB functionality in VirtualBox
is to run it as a root user.

Press
ALT+F2 
and then enter "gksu VirtualBox

that should run your virtualbox as a root user.
you wont see your virtual machines to fix that you'll have to create a link between the virtualbox config folder in your profile and the one in the root user.

I did it a while back but I dont remember the exact command but you can goole about "ln" command that is used to create links.

---

