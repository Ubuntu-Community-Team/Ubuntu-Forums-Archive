---
title: "Move Window Control To The Left on Oneiric Gnome-Shell?"
date: 2011-10-18
forum: Desktop Environments
---

### Post by karmila on 2011-10-18
The question is the same as on the title :)
I feel it will be more consistent to put window control to the left because on gnome-shell we manage windows by pointing cursor to the top-left corner.

It is default in unity session but not in gnome-shell.
I don't see how to do this on gnome-tweak-tool.

Thanks.

---

### Post by Rasa1111 on 2011-10-18
[http://geekum.wordpress.com/2011/05/25/how-to-move-close-button-in-debian-gnome-shell-to-left-like-ubuntu/](http://geekum.wordpress.com/2011/05/25/how-to-move-close-button-in-debian-gnome-shell-to-left-like-ubuntu/)

Just follow that.
and instead of just "close:"
you can add minimize/maximize to it also, if not already there.
so it would be  > close, minimize, maximize:Hope it helps.

edit: you can also use dconf-tools/ dconf-editor. 

or this command alone should get you there..
```

gconftool-2 -s -t string /desktop/gnome/shell/windows/button_layout "close,minimize,maximize:"
```

---

### Post by karmila on 2011-10-18
> **Rasa1111 said:**
> [http://geekum.wordpress.com/2011/05/25/how-to-move-close-button-in-debian-gnome-shell-to-left-like-ubuntu/](http://geekum.wordpress.com/2011/05/25/how-to-move-close-button-in-debian-gnome-shell-to-left-like-ubuntu/)

Just follow that.
and instead of just "close:"
you can add minimize/maximize to it also, if not already there.
so it would be  Hope it helps.

edit: you can also use dconf-tools/ dconf-editor. 

or this command alone should get you there..
```

gconftool-2 -s -t string /desktop/gnome/shell/windows/button_layout "close,minimize,maximize:"
```

Hi Rasa,

Thanks it works like a charm :D
Btw, i use gconf-editor instead of dconf-editor.

About window title, is it theme built in or i also can change it from gconf-editor?

---

### Post by Rasa1111 on 2011-10-18
No problem Karmila. :)

I'm not positive on the window title, I haven't messed with that at all in Gnome3 yet.
But what do you mean by "change it"? 
The font? or something else?

---

### Post by karmila on 2011-10-18
> **Rasa1111 said:**
> No problem Karmila. :)

I'm not positive on the window title, I haven't messed with that at all in Gnome3 yet.
But what do you mean by "change it"? 
The font? or something else?

Ah sorry, what i meant was title position.
With the buttons on the left it looks a little bit crowded there :lolflag:

---

### Post by Rasa1111 on 2011-10-18
ohh right. 
I don't know how to change that yet, sorry my friend. 

I have had this page saved for awhile, that has a lot of info on changing things on GS,
you might find it useful?[http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html)

also, just glancing at that page again, I see his titles are in the center.. 
so hopefully the info on how to, is there! lol

Someone smarter will probably come along and tell us anyway though. :)

Good luck. :)

---

### Post by karmila on 2011-10-18
> **Rasa1111 said:**
> ohh right. 
I don't know how to change that yet, sorry my friend. 

I have had this page saved for awhile, that has a lot of info on changing things on GS,
you might find it useful?[http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html)

also, just glancing at that page again, I see his titles are in the center.. 
so hopefully the info on how to, is there! lol

Someone smarter will probably come along and tell us anyway though. :)

Good luck. :)

That is a comprehensive how-to.
I will take a look on that and see what can i do :D

Thank you.

---

### Post by tancrackers on 2011-11-08
Download gconf-editor and go to desktop, gnome, shell, windows, button and the setting should be something similar to :close,maximize,minimize. Change it to close,minimize,maximize:
In other words, put the buttons to the left of the colon.

Source: [http://askubuntu.com/questions/69582/move-gnome-shell-window-close-button-to-left/77351#77351](http://askubuntu.com/questions/69582/move-gnome-shell-window-close-button-to-left/77351#77351)

---

