---
title: "Volume control icon"
date: 2006-01-24
forum: Desktop Environments
---

### Post by albertoramirez on 2006-01-24
Hello:

I've lost my volume control icon, the little speaker at the top right corner next to the clock.  I've tried to get it again configurind the panel and adding a volume control , and it gets there, but no icon, so I have to pick again and again until the volume slide appears.

Any idea?

Thanks

---

### Post by ogregore on 2006-01-24
alberto -
 
I think it has to do with your icon theme.  I know that if I use some themes my volume applet icon "disappears".  Try a different icon theme and it should reappear, in fact if you have opened it many times you may find that you have a bunch of icons there once you change themes.
 
Cheers
Ogre

---

### Post by albertoramirez on 2006-01-25
Thanks!  You where right!

There are some icon themes that don't display that icon.

---

### Post by jcaceres on 2006-03-01
I had the same problem and i resolve it ..:p 
follow the instrunctions ..
You have to know the "icons theme name"  that is un use on your desktop. That you can do it with:

 ls -l $HOME/.icons 
or system --> Administration --> Theme --> Theme Details --> Icons
:-k 
Then you  execute .. 

cd /usr/share/icons/gnome && tar -cvf $HOME/.icons/<ICON_THEME_NAME>/vol.tar `find ./ -type f -name "*vol*" -print `

Where ICON_THEME_NAME is the current "icons theme name".

then you execute .. 

cd $HOME/.icons/<ICON_THEME_NAME>&& tar -xvf vol.tar

and it's ready ... 

Please send a feedback to know if it works ...:mrgreen:

---

### Post by Ramses de Norre on 2006-03-01
Or add "Inherits=gnome" to your index.theme file in your theme directory (~/.themes/theme_name)

---

