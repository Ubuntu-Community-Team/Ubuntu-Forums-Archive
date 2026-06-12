---
title: "E17 might be my only choice now..."
date: 2006-01-10
forum: Desktop Environments
---

### Post by nalmeth on 2006-01-10
hehe..

yes, so I installed the E17 DE from the howto in the customization and tips forum of course, and I must say, its very sweet. 
I had been playing around a little bit with it, and at one point, got out, and went into both KDE and GNOME to make sure everything was cool. It was, so I continued to play around. 
All I had done, was copy all the animated backgrounds available on their site into ~/.e/e/backgrounds. I had added nothing else. I had however enabled a few dorment modules.
So now, what brings me here, is that an attempt to login to GNOME gave me the old ICEauthority error. KDE gave me an error window with a red X, which I have encountered before but cannot recall. It is blocked by the splash-screen, and quickly reverts back to GDM. XFCE gave me the ICEauthority error screen aswell. 
I knew full well that I was toying with experimental packages, and I knew full well what was being risked. 
All while this was going on, I was able to use E17 just fine. 

I ran:
sudo chown nalmeth /home/nalmeth/.ICEauthority

This allowed me to log in normally.

Can anyone offer an explanation as to why this happened?
I am extremely tired, so I am going to bed. I have edited this message as I cannot recall how to delete it. As it is not terribly important, reply to or ignore it as you will :)

---

### Post by Ampersand on 2006-01-10
It's possible that if you were using one of the installation scripts for E17, and you ran the wrong bit as root, that the ownership of some files in your home directory got changed to root.

---

