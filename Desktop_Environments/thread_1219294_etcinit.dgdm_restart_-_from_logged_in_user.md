---
title: "/etc/init.d/gdm restart - from logged in user"
date: 2009-07-21
forum: Desktop Environments
---

### Post by 4dplane on 2009-07-21
Hi,

I need to restart gdm from a user that is logged into the GUI account. Meaning I have the command in a gnome-panel button:

/etc/init.d/gdm restart

when I run this command the session logs out but never back in. Is there a way around this problem?

---

### Post by bacil on 2009-07-21
shuldnt you do it as root ... eg use sudo ?

---

### Post by 4dplane on 2009-07-21
I have the user added to visudo and I use sudo in the command. I just forgot to wright it in the post.

GDM shuts down but it never restarts. If I run this same command in an terminal from a different machine it completely works. So it has to do with the fact that its the local user calling gdm resart.

Thanks,
4D

---

### Post by bacil on 2009-07-21
Did you try Ctrl+Alt+F7 after restart ? meaning switching console to graphical display ?

---

### Post by 4dplane on 2009-07-21
Um no...

so I hit that key combo when I am logged in and it takes me to a screen with a blinking courser. 

If I run sudo /etc/init.d/gdm restart I am taken to a screen with a blinking courser.

In both casses the key combo does not do anything when all I see is the courser.

Is this right? 

4D

Edit***
o is the key combo running different init levels?

---

