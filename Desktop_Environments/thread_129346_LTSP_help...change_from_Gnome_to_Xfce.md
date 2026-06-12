---
title: "LTSP help...change from Gnome to Xfce"
date: 2006-02-13
forum: Desktop Environments
---

### Post by czimmerman on 2006-02-13
Hello all,

First off, first post here. I've been a long time supporter of Ubuntu, and honestly, between the forums and the wiki have been able to get all the help I needed.

This time though, the other IT guys and myself are stuck and have been researching all day and can not find out any information on this one topic.

We decided to setup LTSP for some of the supervisors that only read need access to e-mail and OO.o. So we decide to go the easy route and download Edubuntu (since its pre-configured pretty much and all) and install it on our one server. 

After launching a couple systems, we realize our network isn't that strong after all, but would still like to use this approach of thin clients. We talk it over, and pretty much all agree that giving Xfce a shot would be the best move. However, we have no idea where to make the changes so that the "LTSP Display Manager" will allow us to chose Xfce as a session. 

Can anyone out there help us out?

---

### Post by Jimmey on 2006-02-13
Here's how I got XFCE working ( assumes you have Gnome ).

First things first. I got XFCE.

> sudo apt-get install xubuntu-desktop.

Second things second. I logged out.

( You could try CTRL + ALT + BACKSPACE, then typing "startx xfce" in the fullscreen terminal windows there. )

Third : I can't remember what the origional Gnome login menu looks like. But, there should be a "sessions" menu(button?) or something similar. Click that - Then click on "XFCE".

Fourth. Avoid everything screwing up. ALT + F2. Then type 
> xfdesktop
and the same, but this time type 
> nautilus --no-desktop.

I hope that's the information you're after.

---

