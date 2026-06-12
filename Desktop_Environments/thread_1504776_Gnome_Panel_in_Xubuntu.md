---
title: "Gnome Panel in Xubuntu"
date: 2010-06-08
forum: Desktop Environments
---

### Post by llamas612 on 2010-06-08
I posted this in General Help, but now i realized its probably more appropriate for this sub forum.

So I've been using XFCE instead of GNOME lately, but I miss the gnome-panel. So, I installed gnome-panel and then ran it. It works perfectly fine except that when I log into my computer, it will first run xfce-panel, then after some time, it will run gnome-panel. Its not a huge deal, but i don't like the fact that it takes longer to boot up and that xfce-panel and gnome-panel are running at all times. Oh and i'm running Xubuntu 10.04 by the way.

Any suggestions? Thanks in advance

---

### Post by azertyh on 2010-06-08
hi,
you can get gnome applets in xfce panel by installing xfapplet. it's in synaptic.

---

### Post by llamas612 on 2010-06-08
Thanks for the reply.

I've seen xfapplet, but i'm actually trying to use gnome-panels instead of the xfce-panel completely. I just don't like the way xfce panels works.

---

### Post by error420 on 2010-06-08
> **llamas612 said:**
> Thanks for the reply.

I've seen xfapplet, but i'm actually trying to use gnome-panels instead of the xfce-panel completely. I just don't like the way xfce panels works.

try this.... 

1) alt+f2 then type gconf-editor 
2) select desktop >> gnome >> session >>> required components
3) finally erase the value in "panel" 
4) change it to "gnome-panel" without the quotes
5) restart.

Hope this helps. Please if you have time, write back and let me know if it was a pass or fail.

---

### Post by kerry_s on 2010-06-08
all you need to do is kill xfce4-panel & save the session.

in terminal or alt+f2
killall xfce4-panel

now look through your menus, i think it's called "application startup" now, sorry can't remember.

---

### Post by kerry_s on 2010-06-08
> **error420 said:**
> try this.... 

1) alt+f2 then type gconf-editor 
2) select desktop >> gnome >> session >>> required components
3) finally erase the value in "panel" 
4) change it to "gnome-panel" without the quotes
5) restart.

Hope this helps. Please if you have time, write back and let me know if it was a pass or fail.

i can tell you its a fail, gconf-editor is for gnome, we're talking xfce4 here.

---

### Post by SlidingHorn on 2010-06-09
> **kerry_s said:**
> i can tell you its a fail, gconf-editor is for gnome, we're talking xfce4 here.

...xfce4's version of gconf-editor is xfce4-settings-editor.  Do what error420 suggested, only replace gconf-editor with xfce4-settings-editor. :)

---

### Post by llamas612 on 2010-06-11
Thanks for the responses guys.

I ended up going the "kill xfce-panel and save session" route. I tried using the xfce settings editor but its set up much differently than gconf-editor, so i wasn't able to find the appropriate string to edit.

---

