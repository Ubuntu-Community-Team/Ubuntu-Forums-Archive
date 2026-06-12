---
title: "It is possible to set a default Nautilus windows size?"
date: 2007-08-06
forum: Desktop Effects &amp; Customization
---

### Post by srg84 on 2007-08-06
I mean, for example, default window size = 640x480, when I open a new Window.

---

### Post by srg84 on 2007-08-06
I Have just found it!:


sudo apt-get install devilspie

    mkdir ~/.devilspie

    gedit /HOME/USER/.devilspie/Datos.ds


(if
(matches (window_name) DATA
(begin
(unmaximize)
(geometry "800x600")
)
)

Execute: devilspie -a

I hope this works, I'll try it when i Arrive Home

---

### Post by srg84 on 2007-08-07
It Works!, I Will explain HowTo Set a default nautilus size.

FIrst of all, If you have an icon called Computer in your desktop and you want to see it always as 800x600 when you open its window, do this:

In console:

 sudo apt-get install devilspie

mkdir ~/.devilspie

gedit /HOME/USER/.devilspie/Computer.ds


(if
(matches (window_name) Computer
(begin
(unmaximize)
(geometry "800x600")
)
)

And execute: devilspie -a

PD:replace /HOME/USER with your user path.

If you have another icon on desktop that you want to have its window resized, you only have to repeat the method changing the word "Computer" with the new one.

---

### Post by Ub1476 on 2007-08-07
Nice I want to change the default terminal size:P

---

### Post by srg84 on 2007-08-07
Maybe this helps you:

[http://bitelia.com/2007/05/31/devilspie-y-a-embeber-un-terminal-en-tu-escritorio/](http://bitelia.com/2007/05/31/devilspie-y-a-embeber-un-terminal-en-tu-escritorio/)

---

### Post by maikito on 2008-02-20
hi there, 

there is a more easy, natural way of doing  this.

right click on the icon you use to open nautilus and select properties

where it says command

just paste this


                   nautilus --no-desktop   --geometry=700x500

and then change the geometry for what you want



this is
 my first post yeah     :D  :guitar:

---

### Post by maikito on 2008-02-20
ok 

i forgot...


for the terminal window do it similar.


right click on the icon and then


                       gnome-terminal --geometry=92x38 --hide-menubar


(i like to hide the menubar)

cheers  :D

---

### Post by DaymItzJack on 2008-02-20
Also you could use compiz fusion and not use devilspie. ;)

---

