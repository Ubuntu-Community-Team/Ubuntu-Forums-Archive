---
title: "Help with cairo dock customization"
date: 2009-05-24
forum: Desktop Environments
---

### Post by dox_drum on 2009-05-24
Hi everybody!

Yesterday I download a set of icons and spent 15 min. changing the look of my cairo-dock (I changed one-by-one the icons of the applications). However, when I open a web browser a new icon appears and it is one of the default configuration. Any idea about how to solve it?

The version of the dock I've installed is the one in the repositories, because the second version does not work well (I assume due to my graph card...).

Less important but still a concern, the only theme of my dock is the cairo theme... when I install it on Intrepid there were about 10 different themes. Does any one know what is going on?

Than you very much!

---

### Post by celticbhoy on 2009-05-24
Did you try v2 with -c option ???

---

### Post by dox_drum on 2009-05-24
> **celticbhoy said:**
> Did you try v2 with -c option ???

I'm sorry man! What do you mean with v2?

---

### Post by dox_drum on 2009-05-24
> **celticbhoy said:**
> Did you try v2 with -c option ???

not really. Let me try it!

---

### Post by fabounet on 2009-05-25
> when I open a web browser a new icon appears and it is one of the default configuration
do you have a launcher for this appli in your dock ? if so, just activate the "mix launcher and appli" option, in the Taskbar module ;)
otherwise, just create a firefox.png (or firefox-3.0.png, what is important is the class of the appli) somewhere where the dock can find it (~/.config/cairo-dock/current_theme/icons by default), and activate the "overwrite X icons" option
then when you launch this appli it will take this icon instead of the X one.

---

