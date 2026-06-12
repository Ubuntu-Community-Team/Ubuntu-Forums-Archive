---
title: "disabling some compiz effects"
date: 2006-08-02
forum: Desktop Environments
---

### Post by Vlatko on 2006-08-02
ok i really like compiz and all the eye candy i have with it. but some effects are reaaally annoying and i'd like to turn them off ASAP. i know there is a control panel for this usng this command ```
gconf-editor &
``` but i just can't seem to find my way around it. i'm a newbie in linux after all.

firstly i'd like to disable the annoying woobly effect that opens with opening menus. whether it's right clicking on the desktop, opening a menu from a application...it's just too much and quite annoying.

second i'd like to disable the same effect that happens when you get some sort of a notification. again completely unnecessary and i just don't like it. :)

i don't mind the wooble effect on dragging windows adn such  but these two things are really annoying.

anyone able to help me with this?

thanks!

---

### Post by tubo on 2006-08-02
in Gconf-editor, go to

apps - compiz - general - allscreens - options

and find the active_plugins key. Double click and remove "wobbly" from the list, close the editro, done.

tubo

---

### Post by tubo on 2006-08-02
edited.

---

### Post by mcduck on 2006-08-02
> **tubo said:**
> edited.
If you are running Compiz from QuinnStorm's repositories, you might also want to install couple of useful apps, Gset-Compiz is a graphical tool for configuring Compiz and Gcompiz-themer is a tool for configuring Compiz themes :)

---

### Post by Vlatko on 2006-08-02
> **mcduck said:**
> If you are running Compiz from QuinnStorm's repositories, you might also want to install couple of useful apps, Gset-Compiz is a graphical tool for configuring Compiz and Gcompiz-themer is a tool for configuring Compiz themes :)
i'm not sure from which repositories, i followed this here guide to set it up [http://www.ubuntuforums.org/showthread.php?t=222034&highlight=xgl](http://www.ubuntuforums.org/showthread.php?t=222034&highlight=xgl)

where can i find those apps?

@tubo, will that completely disable the wobble effect? cause i just hate it in the menu opening and new notifications. i don't mind other wobbly effects. :)

---

### Post by mcduck on 2006-08-03
> **Vlatko said:**
> i'm not sure from which repositories, i followed this here guide to set it up [http://www.ubuntuforums.org/showthread.php?t=222034&highlight=xgl](http://www.ubuntuforums.org/showthread.php?t=222034&highlight=xgl)

where can i find those apps?

@tubo, will that completely disable the wobble effect? cause i just hate it in the menu opening and new notifications. i don't mind other wobbly effects. :)
It looks like you already have the right repositories, so you should be able to install those apps with apt-get or synaptic.

And yes, disabling wobbly plugin will disable wobble effect completely. Just install gset-compiz and you can tune the effect to your liking and disable it for those window types you don't want to wobble.

---

