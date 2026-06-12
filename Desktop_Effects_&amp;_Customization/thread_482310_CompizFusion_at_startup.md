---
title: "CompizFusion at startup"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by timo1023 on 2007-06-23
I just installed compizfusion, and I want it to startup at startup, so I added compiz --replace to the session thing and it works fine, but I don't have my beryl windows borders, and I dont see how to change the windows borders through CompizConfig, they are only using the metacity ones. How can I do this without running beryl and compizfusion?

---

### Post by mid_night gypsy on 2007-06-23
Howdy,
 I hope some one can answer this one? I just converted from Beryl. Although  a little confusing ( Compizfusion) I do  like it. In sessions I added compiz --replace emerald. It works (kindof) It's loads very,very slow.Hope someone can shed some light on this one?
                                                                                                    Much Thanks,gypsy

---

### Post by bitzer on 2007-06-25
You have to modify /usr/bin/compiz. From terminal:

sudo gedit /usr/bin/compiz

In gedit:

goto line 511 and replace "gtk-window-decorator" with "emerald"
goto line 515 and replace "gtk-window-decorator" with "emerald"

Restart GNOME and you're done!

---

### Post by mid_night gypsy on 2007-06-25
bitzer,
 Thanks for reply. Did what you said and still no luck? It (compizfusion) boots with emerald with this command compiz --replace -c emerald & .....I try your suggestion with command compiz --replace..But either way takes 'bout 2-3 min. any tips. Thanks again,gypsy

---

### Post by sambehera on 2007-07-14
thanks mid_night gypsy 

> compiz --replace -c emerald &

did the trick for me

---

### Post by walkerk on 2007-07-14
you say it takes 2 - 3 minutes to load?

i had a similar problem because i didn't remove compiz & beryl before installing compiz-fusion.

you might try removing everything compiz/compiz fusion/beryl related through synaptic.. reboot.. re-install compiz-fusion..

this worked for me..

---

### Post by keenish27 on 2007-08-05
i typed compiz --replace -c emerald &   and compizfusion and emerald are running fine, tho i don't know how to edit my emerald themes now.....


EDIT:  nevermind, i'm dumb...it was under system > preference

---

