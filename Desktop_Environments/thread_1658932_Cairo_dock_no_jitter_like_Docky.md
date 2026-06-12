---
title: "Cairo dock no jitter like Docky"
date: 2011-01-03
forum: Desktop Environments
---

### Post by miousername on 2011-01-03
Hi at all,:guitar:

I've notice that cairo dock has  jitter when you move the mouse over the Dock. Indeed if you install Gnome Do (Docky) you notice that when you move the mouse over the bar the effect is very smooth. I don't understand why cairo dock is less smooth in movement  but i finally found a solution:

1- Close cairo-dock bar;

2- Go to ~/.config/cairo-dock/current_theme/

3- Open the file cairo-dock.conf with gedit

4- Now  press ctrl+f and insert in the search:  refresh frequency

5- Now you have to modify the line:

#i-[5;60] Refresh frequency when mouving cursor into the dock :
#{in Hz. This is to adjust regarding your CPU power.}
refresh frequency=35

in thi s way:

#i-[5;120] Refresh frequency when mouving cursor into the dock :
#{in Hz. This is to adjust regarding your CPU power.}
refresh frequency=120

6- save the modification;

7- start cairo-dock;

et voila your dock works very good!

 The difference is noticable!

Thank you and bye at all!

This is an example of bad programmation, a lot of possibility to configure the dock but no one of this it's adequately cured.

---

### Post by Syirrus on 2011-02-08
> **miousername said:**
> Hi at all,:guitar:

I've notice that cairo dock has  jitter when you move the mouse over the Dock. Indeed if you install Gnome Do (Docky) you notice that when you move the mouse over the bar the effect is very smooth. I don't understand why cairo dock is less smooth in movement  but i finally found a solution:

1- Close cairo-dock bar;

2- Go to ~/.config/cairo-dock/current_theme/

3- Open the file cairo-dock.conf with gedit

4- Now  press ctrl+f and insert in the search:  refresh frequency

5- Now you have to modify the line:

#i-[5;60] Refresh frequency when mouving cursor into the dock :
#{in Hz. This is to adjust regarding your CPU power.}
refresh frequency=35

in thi s way:

#i-[5;120] Refresh frequency when mouving cursor into the dock :
#{in Hz. This is to adjust regarding your CPU power.}
refresh frequency=120

6- save the modification;

7- start cairo-dock;

et voila your dock works very good!

 The difference is noticable!

Thank you and bye at all!

This is an example of bad programmation, a lot of possibility to configure the dock but no one of this it's adequately cured.

Thank you, this was exactly what I was looking for!

---

