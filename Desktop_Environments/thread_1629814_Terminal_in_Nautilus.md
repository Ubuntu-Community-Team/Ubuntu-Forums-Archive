---
title: "Terminal in Nautilus"
date: 2010-11-24
forum: Desktop Environments
---

### Post by mehta_april on 2010-11-24
How to embed GNOME-TERMINAL(ICON) in Nautilus..?
Further, that must open terminal in the current-directory(when clicked), same directory as the nautilus do !

How to achieve this..?

---

### Post by BcRich on 2010-11-24
hi
if i understand your question, are you asking how to open the terminal from nautilus with terminal pointing to the current directory?
if that is what you'd like to achieve there is a useful system config tool called ubuntu tweak [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
if you install ubuntu tweak 
(inside ubuntu tweak) under system > nautilus > and check Nautilus with Open Terminal 
(NB this is ubuntu tweak 0.4.8)
then when you right click in any directory in Nautilus in the menu will be an option that says "Open in Terminal"

---

### Post by kaustavdm on 2010-11-24
I use the same thing as suggested by BcRich and it is very helpful :D 

Just FYI, I use Ubuntu Tweak 0.5.7 and the same options are named a bit differently. In Ubuntu Tweak, it is now in System > Nautilus Settings > Nautilus Extensions > Open folder in terminal.

---

### Post by mikewhatever on 2010-11-24
You'd probably need to develop skills and write your own or modify the existing nautilus plugin. The plugin is called **nautilus-open-terminal** and it's in the repositories.
Funny people think it's an Ubuntu Tweak feature.;)

---

### Post by stinkeye on 2010-11-24
There is also Nautilus Terminal which embeds a terminal in nautilus.
F7 to toggle on/off.
[**_[COLOR="DarkRed"]Nautilus Terminal[/COLOR]_**]("http://www.omgubuntu.co.uk/2010/09/nautilus-terminal-gui-meets-cli/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg%21+Ubuntu%21%29") <---How to install.

---

### Post by kaustavdm on 2010-11-24
> **mikewhatever said:**
> You'd probably need to develop skills and write your own or modify the existing nautilus plugin. The plugin is called **nautilus-open-terminal** and it's in the repositories.
Funny people think it's an Ubuntu Tweak feature.;)
I never did for once think it to be a Ubuntu Tweak feature. The reason I suggested/supported it was for the easy interface Ubuntu Tweak features to enable some Nautilus scripts.

---

### Post by kaustavdm on 2010-11-24
> **mikewhatever said:**
> You'd probably need to develop skills and write your own or modify the existing nautilus plugin. The plugin is called **nautilus-open-terminal** and it's in the repositories.
Funny people think it's an Ubuntu Tweak feature.;)
I never did for once think it to be a Ubuntu Tweak feature. The reason I suggested/supported it was for the easy interface Ubuntu Tweak features to enable some Nautilus scripts.

---

### Post by stinkeye on 2010-11-24
> **kaustavdm said:**
> I never did for **once** think it to be a Ubuntu Tweak feature. The reason I suggested/supported it was for the easy interface Ubuntu Tweak features to enable some Nautilus scripts.

But you did reply twice. ;)

---

### Post by kaustavdm on 2010-11-24
Lol. My connection had timed out and I had accidentally refreshed the page and resubmitted the form :-D

Still I hold that I had not thought of it even once :p

Btw, F7 toggle is not working on my desktop. If not, what am I missing?

---

### Post by stinkeye on 2010-11-24
You should be able to choose **Embed Terminal** from the view menu.

If you installed as from my previous post(I've edited to make clearer) and no menu item try
in the terminal```
pkill nautilus
``` 
and reopen nautilus.

---

### Post by kaustavdm on 2010-11-24
Thanks! It's better than opening a folder separately in Terminal :)

---

### Post by stinkeye on 2010-11-24
> **kaustavdm said:**
> Thanks! It's better than opening a folder separately in Terminal :)
Ahh, you got it.
Yeah for some things it's good to have a terminal open for the directory your
in rather than opening a terminal and cd-ing.

...and if I've told you once, I've told you twice............. :p

---

### Post by kaustavdm on 2010-11-24
..but you wrote it once :p lol
Enjoying the freedom from cd-ing :D

---

