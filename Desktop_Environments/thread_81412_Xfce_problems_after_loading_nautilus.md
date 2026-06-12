---
title: "Xfce problems after loading nautilus"
date: 2005-10-24
forum: Desktop Environments
---

### Post by nsa_767 on 2005-10-24
Hi there,

I (for some unknown reason) started up nautilus from within an Xfce session. Then this happened:

1. Upon loading nautilus, my Xfce background changed to the background I have in Gnome, even though the Xfce setting show that I still have my old background.

2. I proceeded to close nautilus and exited Xfce. Then, reentering Xfce, the problem was still not sorted.

3. Checked the System Monitor and found that there was still a nautilus process running, so I killed it and restarted my PC.

4. Entered Xfce, now I have no background, just a plain ubuntu-brown solid colour. Also, nothing happens if you left click / right click on the desktop area.

Please help, this annoying me!

---

### Post by aysiu on 2005-10-24
Type Alt-F2 to get the Run dialogue.
Then run this command ```
xfdesktop
``` When you log out, make sure you save your session.

---

### Post by nsa_767 on 2005-10-24
Thank you, that's sorted the problem! 

BTW, just out of curiosity, can you perhaps explain me why loading nautilus caused all those "problems"? What other things can possibly cause this sort of thing? 

It's not merely loading a Gnome app, since I've loaded many Gnome and KDE apps without this sort of thing happening....

Well, thanks again... :)

---

### Post by chanders on 2005-10-24
This "problem" you have is because, Nautilus is not only a file manager, but it also controls the desktop. When you ran Nautilus, it opened the file manager but also took control of the desktop.

My guess is when you exited, your session was saved which is why Nautilus restarted. 

At least now you have everything back in order....  :D

---

### Post by sambler on 2005-10-27
I experienced exactly the same problem, and was grateful to find the solution here on the Ubuntu forums. The problem persisted even though I made sure to uncheck the "save session" box on exiting from xfce. Before trying here, I poured through all of the xfce configuration files that I could find in ~/.config/, but I could find no clue as to how in fact nautilus maintains control even after it is shut down.

It must overwrite a line somewhere in the xfce config files. Can someone tell me which one?

Thanks.

---

### Post by josys36 on 2006-10-27
I never found a solution to this either. And what is funny, is that it starting happening for no reason.

Jason

---

