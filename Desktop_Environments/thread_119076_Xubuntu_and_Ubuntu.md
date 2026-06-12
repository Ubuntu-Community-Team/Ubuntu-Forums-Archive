---
title: "Xubuntu and Ubuntu"
date: 2006-01-18
forum: Desktop Environments
---

### Post by krypto_wizard on 2006-01-18
I recently installed Xfce desktop just to play around with. This morning there was kernel update from ubuntu. When I restarted my computer, while booting 
Ubuntu became Xubuntu and its colow was blue. i,e. Instead of showing brown Ubuntu while booting it showed me a blue Xubuntu.

When the login screen came it was back to the normal human theme of Ubuntu in Yellow and Brown.

How can I win back my Ubuntu back on the screen while booting.

Every help is appreciated.

Thanks

---

### Post by newuser111 on 2006-01-18
try sudo dpkg-reconfigure linux-image-$(uname -r) 


not sure if you have to remove the xubuntu artwork package, it is listed in synaptic as xubuntu-artwork-usplash

---

### Post by krypto_wizard on 2006-01-18
Nothing seems to work. I have removed everything from xubuntu-desktop and Xfce but still while booting the xubuntu screen shows up with a mouse in between the ubuntu logo.

I want to get back my Ubuntu back.

Can anybody please help me

[QUOTE=newuser111]try sudo dpkg-reconfigure linux-image-$(uname -r) 


not sure if you have to remove the xubuntu artwork package, it is listed in synaptic as xubuntu-artwork-usplash[/QUOTE]

---

### Post by chrism7 on 2006-01-19
I don't have an answer unfortunately, but the same thing happens to me.  Mine seems to change between ubuntu, xubuntu and even edubuntu (I have xfce4 and edubuntu-desktop (for my son) installed).  I also have the blue instead of brown now.  It doesn't bother me, but I'll be interested to hear the answer as well.

---

### Post by byen on 2006-01-19
ok..here is something that would help you
[http://www.ubuntuforums.org/showthread.php?t=113250](http://www.ubuntuforums.org/showthread.php?t=113250)
Please let me know in that thread if it works...Hope it helps.

---

### Post by krypto_wizard on 2006-01-19
Thanks dude!!!

[QUOTE=byen]ok..here is something that would help you
[http://www.ubuntuforums.org/showthread.php?t=113250](http://www.ubuntuforums.org/showthread.php?t=113250)
Please let me know in that thread if it works...Hope it helps.[/QUOTE]

---

