---
title: "Cairo-Dock"
date: 2009-05-28
forum: Desktop Environments
---

### Post by Bankai56 on 2009-05-28
Hey i looked and cairo dock and it is pretty sweet.
Now i don't like it if it is instead of the bar at the bottom of the screen, but is it possible, that i can put it in widget layer and still keep the bar. Would look amazing for me!
Thanks in advance!

---

### Post by Viva on 2009-05-28
Not sure what you're trying to do, can you explain a bit more?

---

### Post by picopir8 on 2009-05-28
Cairo-dock is independent of the panel bar so you can have both, neither, or any combination of the two.  I ran cairo-dock just above my bottom panel but as I began using cairo-dock more, I realized that the bottom panel had little value so I got rid of it.

You can also move cairo-dock to the top or sides of your display if you really want.

If you get cairo-dock, skip the one in the ubuntu repo and go get the 2.0.3 and be sure to get the addon pack to so you get all the effects and additional tools.

---

### Post by Boondoklife on 2009-05-28
Or check out gnome-do and click the docky option. Slick and seems to run lighter!

---

### Post by Bankai56 on 2009-06-01
OK i got cairo dock.
I will try gnome do later sorry....
Now the theme ist just bad. How do i change that and how can i add stuff to it i just can't find out.
And how do i add it to the widget layer?
Befor i foget where can you download themes?
Thanks

---

### Post by irons on 2009-06-01
I removed all my panels from the gnome desktop and only use Cairo dock now, still got some tweaking left, for some reason it randomly changes some of my icons on restart, even if I saved my theme and made a theme file for it.

Next thingt to fix is the "light" under the icon that indicates that I have a runnin application from it, still banging my head for that one :\

---

### Post by picopir8 on 2009-06-01
There seems to be a bug in cairo-dock that causes it to revert back to the default theme.

The workaround I used was first save the theme the way you like it.
then from a command prompt type:

sudo rm -rf /usr/share/cairo-dock/themes/_default_
sudo cp -rf ~/.config/cairo-dock/themes/YOUR_THEME_HERE /usr/share/cairo-dock/themes/_default_

---

### Post by fabounet on 2009-06-02
which version ?
did you try 
```
chmod -R 777 ~/.config/cairo-dock
``` ?

PS : the task indicator is under ... Indicators ;-)

---

