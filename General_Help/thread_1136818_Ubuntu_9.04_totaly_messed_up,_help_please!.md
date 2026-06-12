---
title: "Ubuntu 9.04 totaly messed up, help please!"
date: 2009-04-25
forum: General Help
---

### Post by cozmoz on 2009-04-25
Hi, the problem I'm having is very weird. I'm able to boot up ubuntu but then it all gets messed up. I can't login and the screen looks totaly screwed.
     What I did before this happend was opening a billiard game I dont remember its name, but the frames in the game window just flashed, like I was having to low framerate for the game. So I closed the game, then the screen froze and now I cannot get on again. Please I need help to fix this.

Sorry for bad english!

---

### Post by pastalavista on 2009-04-25
Next time you boot, choose recovery mode and run 'xfix' (last item on the menu)

---

### Post by cozmoz on 2009-04-25
> **pastalavista said:**
> Next time you boot, choose recovery mode and run 'xfix' (last item on the menu)

Thanks for the tip, it didnt gave any results though :(
Is there anything else I should try?

---

### Post by Alias1407 on 2009-04-25
If you have a live cd lying around boot into that. Open a terminal and type...
```
sudo passwd
```
...and set a root password

Go System --> Administration --> Login Window, then goto the Security tab, tick the "Allow local system administrator login". Logout and then login with "root" and the password that you had just set.

When you have logged in goto /etc/X11/  (on your mounted drive and not the cd file system)

now you want to look for xorg.conf , open that and see if there are any problems, if you don't understand then just delete xorg.conf, copy xorg.conf.failsafe and rename to xorg.conf

Try that and see if it works, of course you could do all this in a failsafe terminal but it feels easier with a Desktop Manager.

---

### Post by cozmoz on 2009-04-25
> **Alias1407 said:**
> If you have a live cd lying around boot into that. Open a terminal and type...
```
sudo passwd
```
...and set a root password

Go System --> Administration --> Login Window, then goto the Security tab, tick the "Allow local system administrator login". Logout and then login with "root" and the password that you had just set.

When you have logged in goto /etc/X11/  (on your mounted drive and not the cd file system)

now you want to look for xorg.conf , open that and see if there are any problems, if you don't understand then just delete xorg.conf, copy xorg.conf.failsafe and rename to xorg.conf

Try that and see if it works, of course you could do all this in a failsafe terminal but it feels easier with a Desktop Manager.


Okay, this didnt workout. There wasnt a file named xorg.conf.failsafe, so I overwrited it with the xorg.conf file from the CD. Unfortunently the problem is the same, only now it shows the 8.10 background for some seconds then it gets messed up again. ](*,)

BUMP
BUMP

Anyone that got any suggestions? :/Id rather not uninstall everything and start from scratch. And then have in my mind that it might happend again.

---

