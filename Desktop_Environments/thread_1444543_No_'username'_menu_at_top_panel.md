---
title: "No 'username' menu at top panel"
date: 2010-04-01
forum: Desktop Environments
---

### Post by damhamaza on 2010-04-01
Hi Everyone..

Suddenly, my 'username' at the top panel has disappeared. Anyone knows how to put it back there?

See attachment for picture.

I'm using Ubuntu 10.04 Beta....

---

### Post by tom4everitt on 2010-04-01
Since this is a gnome problem, I would try to reset the settings. Gnome keep its settings in 

1. ~/.config
2. ~/.gnome2
3. ~/.gnome2_private
4. ~/.gconf
5. ~/.gconfd

and maybe some other folders as well.

I'm not sure about which settings are kept where, but I would try moving/removing .config and .gconf first. This will of course reset a lot of gnome settings...


You could also have a look in gconf-editor (start it with gconf-editor in terminal), but I didn't find anything there.

---

### Post by Sadu on 2010-04-01
I think u must add this by right clicking on top panel -> add to panel -> Indicator Applet Session

---

### Post by damhamaza on 2010-04-01
> **Sadu said:**
> I think u must add this by right clicking on top panel -> add to panel -> Indicator Applet Session

tried it..not the one

---

### Post by damhamaza on 2010-04-02
the name of the panel is "MeMenu" right?

---

### Post by damhamaza on 2010-04-02
solved. by installing "indicator-me" package, and add to panel "indicator applet sessions"

thanks!!!

---

### Post by elidoperezmd on 2010-09-15
> **damhamaza said:**
> solved. by installing "indicator-me" package, and add to panel "indicator applet sessions"

thanks!!!

thanks, i had the same problem

---

### Post by mbtshoes2011 on 2010-09-15
thanks for sharing this.

---

