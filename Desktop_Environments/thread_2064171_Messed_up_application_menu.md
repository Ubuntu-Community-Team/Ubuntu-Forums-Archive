---
title: "Messed up application menu"
date: 2012-09-28
forum: Desktop Environments
---

### Post by Farinet on 2012-09-28
Recently - after an installation of a new item (lxmed) to Preferences that entire directory of the lubuntu application menu disappeared.

Now, i'd like to know, where the menu.xml file sits that contains the needed infos (as far as i recall in lubuntu there is a slightly different architecture than with a pure lxde); and how i should/could edit it to make re-appear <Preferences>?

I don't like the idea to have to install alacarte (with all that gnome related "garbage" ;)

TIA for any help.

---

### Post by ajgreeny on 2012-09-28
I think the menu file is at /home/*user*/.cache/menus

having looked at it ion the past, I am not sure how easy it will be to see what went wrong, or to put it right.

Also there is no point installing alacarte as it will not work in Lubuntu, or it wouldn't in the past; things may have changed now.

---

### Post by Guilden_NL on 2012-09-30
I run LXMenu on all of my systems so I can make menu changes using the GUI approach.  You might give it a try, I've long forgotten where any of the files reside as this takes care of it for me.

Here's where you can get it: [http://lxmed.sourceforge.net]("http://lxmed.sourceforge.net")

I run Openbox, so for me it's located here: ~/.config/openbox/menu.xml

The system-wide location is here: /etc/xdg/openbox/menu.xml

---

### Post by Farinet on 2012-10-01
> **Guilden_NL said:**
> I run LXMenu on all of my systems so I can make menu changes using the GUI approach.  You might give it a try, I've long forgotten where any of the files reside as this takes care of it for me.

Here's where you can get it: [http://lxmed.sourceforge.net](http://lxmed.sourceforge.net)

I run Openbox, so for me it's located here: ~/.config/openbox/menu.xml

The system-wide location is here: /etc/xdg/openbox/menu.xml

Me too, and it's fine. But i don't see there - in lxmed, i mean - an option to configure the menu structure i.e. the topics (like <applications>, <network>, <graphics> etc).

Cheers.

---

### Post by Farinet on 2012-10-01
> **ajgreeny said:**
> I think the menu file is at /home/*user*/.cache/menus

having looked at it ion the past, I am not sure how easy it will be to see what went wrong, or to put it right.

Also there is no point installing alacarte as it will not work in Lubuntu, or it wouldn't in the past; things may have changed now.

Alacarte now works.

I followed your suggestion and went to */.cache/menus but i didn't find any obvious mistake. Anyway, manipulating a bit around here and there mainly in lxmed now the <preferences> topic returned. I suspect its disappearance might be connected to the fact i installed gnome controll center . . . 

Btw, i also tried the "alacarte way" and while i could nicely activate single programs but not change the menu structure.

---

### Post by Farinet on 2012-10-01
I wanted to say thanks to all who tried to help. My problem in the meantime was resolved, a little bit magically - at least for me.

But, to stay in topic: Is there somewhere a good and coherent explanation how to configure and change the **structure** of the lubuntu (LXDE) application menu?

TIA

---

