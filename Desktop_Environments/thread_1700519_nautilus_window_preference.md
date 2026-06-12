---
title: "nautilus window preference"
date: 2011-03-05
forum: Desktop Environments
---

### Post by rvchari on 2011-03-05
i wish to learn how to make nautilus window top look minimalistic and clean. one of the doubt is how to make the "icon view / list view / compact" pull down menu look like small buttons located on top right corner below the window buttons ?

---

### Post by Krytarik on 2011-03-06
Did you already try "Nauilus Elementary"?:
[http://www.makeuseof.com/tag/nautilus-elementary-simplifies-file-browsing-linux/](http://www.makeuseof.com/tag/nautilus-elementary-simplifies-file-browsing-linux/)

However, it doesn't work on all machines, like mine, I get graphical glitches when scrolling.

---

### Post by rvchari on 2011-03-06
> **Krytarik said:**
> Did you already try "Nauilus Elementary"?:
[http://www.makeuseof.com/tag/nautilus-elementary-simplifies-file-browsing-linux/](http://www.makeuseof.com/tag/nautilus-elementary-simplifies-file-browsing-linux/)

However, it doesn't work on all machines, like mine, I get graphical glitches when scrolling.

i tried it, infact i cant find ny difference, (was it already installed ?!) nyways the list / icon / compact view button is still in pulldown menu form and not as buttons....

---

### Post by bezolaam on 2011-03-06
hello. Mine  problem is completely opposite. I made some customiaztions with my desktop, installed elementary by adding elematary's ppa.
But i dont like that, i would like to return to normal nautilus. How to do it? Anyone?

---

### Post by mcduck on 2011-03-06
> **rvchari said:**
> i tried it, infact i cant find ny difference, (was it already installed ?!) nyways the list / icon / compact view button is still in pulldown menu form and not as buttons....

Then you didn't actually succesfully try it yet.

After installing the Nautilus Elementary packages you need to restart Nautilus to see any difference. If you don't do that you are still just running the normal Nautilus version from RAM (and remember that Nautilus is running all the time when you are in Gnome, even if you don't ave any file manager windows open. It's responsible of the desktop itself...)

That being said, it's still a bit buggy for every day use, at least based on my experience. Browser mode worked quite fine (although getting some features working correctly took a bit of hacking) but the spatial mode restarts Nautilus every time you close one window. Which made it rather annoying, since I prefer the spatial mode.

---

### Post by mcduck on 2011-03-06
> **bezolaam said:**
> hello. Mine  problem is completely opposite. I made some customiaztions with my desktop, installed elementary by adding elematary's ppa.
But i dont like that, i would like to return to normal nautilus. How to do it? Anyone?

Easy fix: [http://askubuntu.com/questions/16578/how-do-i-uninstall-nautilus-elementary]("http://askubuntu.com/questions/16578/how-do-i-uninstall-nautilus-elementary")

---

### Post by bezolaam on 2011-03-06
[mcduck]("http://ubuntuforums.org/member.php?u=17309") thanx it works fine

---

### Post by rvchari on 2011-03-06
> **mcduck said:**
> Easy fix: [http://askubuntu.com/questions/16578/how-do-i-uninstall-nautilus-elementary]("http://askubuntu.com/questions/16578/how-do-i-uninstall-nautilus-elementary")

try to install elegant gnome. its a small package you can tweak nautilus to elementary or normal using that from start > accessories > elegant gnome.
its a user friendly interface.

you get it installed automatically if you have used elegant gnome pack from gnome-look.org

---

### Post by Krytarik on 2011-03-06
> **rvchari said:**
> try to install elegant gnome. its a small package you can tweak nautilus to elementary or normal using that from start > accessories > elegant gnome.
its a user friendly interface.

you get it installed automatically if you have used elegant gnome pack from gnome-look.org
I have the package installed, and I tried all those a while ago. I believe to remember that it doesn't change the general appearance of Nautilus, instead it adjusts itself to the version of Nautilus you are using. But I don't want to re-check it, because the "activation" of Elegant Gnome via its tool simply changes too much. I just use the theme from time to time.

EDIT: Ah, you might have installed NE along with Elegant Gnome by following its install instructions, right!? Check with "dpkg -l|grep nautilus" or via its About dialog which version you have installed, the current one for Maverick is 2.32.0-0ubuntu1.3.

---

### Post by rvchari on 2011-03-07
atlast, i got nautilus elementary working.... but the purpose of the thread i started isnt solved !!! now with NE, the nautilus window has made the ugly pull down menu of icon view / list wiew / compact view hide but i thought i ll get a 3 button icon showing the above items in the top right corner (below window buttons) but nothing is there. is it coz i use global menu ? wonder whats needed after this !

---

