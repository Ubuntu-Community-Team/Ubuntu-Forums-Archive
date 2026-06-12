---
title: "[SOLVED] Creating a KDE or Kubuntu Session on UBUNTU HARDY 8.04"
date: 2008-07-16
forum: Desktop Environments
---

### Post by SSVegito888 on 2008-07-16
Can someone please tell me how to create a KDE or Kubuntu Session on UBUNTU HARDY 8.04.


Thanks,

SSVegito888

---

### Post by benerivo on 2008-07-16
You will need to install either the kde3 or kde4 desktop environment, then log out and then log in to it. In Synaptic package manager, the packages you would want are...

kubuntu-desktop (for KDE3)
kubuntu-kde4-desktop (for KDE4)

or for the 'bare bones' kde environments

kde-core (for KDE3)
kde4-core (for KDE4)

---

### Post by ProbablyX on 2008-07-16
If you mean session as in a KDE stored session:

Open up the system settings in KDE4. click the "Advanced tab" and then session manager.

Select to load manually stored session at login and click apply.

There should now be an option under "Quit" on the K-menu to store your session. This may however be damaged in KDE 4.0 - but it should be there!

---

### Post by SSVegito888 on 2008-07-17
I don't know if I was very clear on my post.


Basically, I am trying to be able to go back and forth between GNOME, KDE, and or Kubuntu.


Thanks,

SSVegito888

---

### Post by aysiu on 2008-07-17
> **SSVegito888 said:**
> I don't know if I was very clear on my post.


Basically, I am trying to be able to go back and forth between GNOME, KDE, and or Kubuntu.


Thanks,

SSVegito888
Yes. Post #2 will allow you to do that.

---

### Post by jacksaff on 2008-07-17
Make sure you have all the relevant packages installed (see first reply) then log out.
At the gdm log-in screen (or kdm if you started with kubuntu) there will be an option to change session type (look for it in the sub menus).
Pick gnome, kde (kde3) or kde4 (or any other desktop environment you have installed) as desired and log in.

---

### Post by stitchmysmile93 on 2008-07-17
Well if you have both installed once your logged into one just go to log out but click start new session. start gnome or kde which ever log in. Once your logged in you can switch back and forth using ctrl+alt f7 and f9. the first one you were logged into will be f7 for default then f9 is the second. And if you have blackbox or any other gui's you can log as many as you want. You can even do ctrl alt f2 and get terminals ...

---

### Post by SSVegito888 on 2008-07-17
Sorry, but I still don't quite get how to save a session in Ubuntu 8.04 Hardy in GNOME.

---

### Post by aysiu on 2008-07-17
> **SSVegito888 said:**
> Sorry, but I still don't quite get how to save a session in Ubuntu 8.04 Hardy in GNOME.
You're not saving a session. You're just logging out and choosing a different session before logging back in again.

More details here:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by SSVegito888 on 2008-07-17
OK, I understand now.


Sorry for the headache,

SSVegito888

---

