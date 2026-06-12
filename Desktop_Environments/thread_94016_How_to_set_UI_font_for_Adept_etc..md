---
title: "How to set UI font for Adept etc."
date: 2005-11-23
forum: Desktop Environments
---

### Post by fourhead on 2005-11-23
Hi, I'm using KDE on my laptop, and I've set KDE to use a rather small font (Bitstream Vera Sans 7px), but all apps that are started with sudo (e.g. Adept or the control center) use a very big font, sometimes so big that the UI becomes unusable because the window is too big to fit on the screen. KDE font sizes are stored in ~/.kderc, and I tried copying thing file to /root, but this didn't help. Can somebody help me?


Tom

---

### Post by 23meg on 2005-11-23
I don't use KDE but you should be able to set KDE preferences (including fonts) for root with ```
sudo kcontrol
```.

---

### Post by fourhead on 2005-11-23
Thanks for your tip, but I forgot to mention that I already tried that. For some reason, when I start "sudo kcontrol" in the konsole, kcontrol is showing me the settings of my normal user account! Don't know what to do about that...


Tom

---

### Post by 23meg on 2005-11-23
That doesn't sound like the expected behavior to me, but since I'm KDE illiterate I can't be sure. Make sure you've terminated all instances of kcontrol with "killall kcontrol" before doing it.

---

### Post by daller on 2005-11-23
sudo does not run the command as su, but with su's priviledges!!! (correct me if I'm wrong!)

Edit: I was wrong, it seems!

I'll just try to look around for a fix!

---

### Post by daller on 2005-11-23
running GUI's with sudo is not recommended!

Have you tried with kdesu, instead?

---

### Post by daller on 2005-11-23
I don't know if this is due to my use of KDE3.5 and Dapper, but su's settings in KDE seems to follow the sudoers changes!

---

### Post by Naneau on 2005-12-07
Hi,

I've experienced the same problem, and first thought it had to do something with DPI settings, or some other weird fontproblem. As it turns out though, some KDE apps use the font settings from the root settings. Those are easily changed by pressing Alt+F2, typing 'kcontrol', and make sure that under 'options', you choose 'run as a different user'. Type in 
'root' and the password for root on your system (this is not the same as your user password, you may have to set a root password first). You now get root's KDE Control center, where you can change the font settings for KDE apps run as root, amongst other things (like the icon set).

Note that doing 'sudo kcontrol' in a console will not have the same effect, as it will only give you superuser priviledges, and not run kcontrol AS root. Also, it's generally a bad idea to 'sudo' your way out of problems, running GUI application as root is usually not the way to go, as daller also noted.

---

### Post by mafitzpatrick on 2006-10-25
Using "kdesu kcontrol" and then editing the font sizes with the resulting control panel works fine for me. You should be able to tell it's the root panel as it will have a different layout (possibly) and have "root" as the username.

Give that a shot and let us know how you get on.

In a related question - why is there no way to get to kcontrol from the menu? The system settings thing does offer some options but misses out on others (like launch feedback).  Worth stating that I transferred from ubuntu to kubuntu.

---

