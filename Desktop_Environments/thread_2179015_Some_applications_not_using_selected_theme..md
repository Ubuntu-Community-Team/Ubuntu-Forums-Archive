---
title: "Some applications not using selected theme."
date: 2013-10-06
forum: Desktop Environments
---

### Post by sudo san on 2013-10-06
Hi,
I installed Lubuntu 13.04 and then decided I wanted to use openbox over the top of it.

I found that all of the applications I used in LXDE did not appear as they did in openbox. I found that I could change the gtk icon theme by adding the line:
```
gtk-icon-theme-name = "zoncolorGreyDark"
```
to the file: .gtkrc-2.0
I was also able to set the theme using ```
gtk-chtheme
```


That solved the problem, except for the Ubuntu Software Centre, update-manager and the Synaptic package manager.

Screenshots:
Ubuntu Software Centre: [http://postimg.org/image/nl8h1j9y9/](http://postimg.org/image/nl8h1j9y9/)
update-manager: [http://postimg.org/image/ya9ranm3d/](http://postimg.org/image/ya9ranm3d/)
Synaptic Package Manager: [http://postimg.org/image/ncl73vonr/](http://postimg.org/image/ncl73vonr/)

How can I resolve this? I'm assuming there is another config file somewhere where I need to set the theme and icon again.

Thanks and any suggestions are welcome.

---

### Post by vasa1 on 2013-10-06
[http://ubuntuforums.org/showthread.php?t=2173126](http://ubuntuforums.org/showthread.php?t=2173126) has something on the topic. I don't know about "Ubuntu Software Center". It's not installed by default on Lubuntu 13.04.

---

### Post by sudo san on 2013-10-06
> **vasa1 said:**
> [http://ubuntuforums.org/showthread.php?t=2173126](http://ubuntuforums.org/showthread.php?t=2173126) has something on the topic. I don't know about "Ubuntu Software Center". It's not installed by default on Lubuntu 13.04.

I've tried adding the extra lines to the settings.ini file (I had to create this file myself and then add the lines) but upon exiting and restarting openbox, there is no difference whatsoever.

Thanks for referencing me that link.:)

---

### Post by vasa1 on 2013-10-06
> **sudo san said:**
> I've tried adding the extra lines to the settings.ini file (I had to create this file myself and then add the lines) but upon exiting and restarting openbox, there is no difference whatsoever.

Thanks for referencing me that link.:)
Could you please provide the full path to the settings.ini file you created?

The applications you're having problems with, Synaptic & Software Center, are the ones that need "administrative privileges". See what you have in **/etc/gtk-3.0/settings.ini**.

Mine looks like this:
```
[Settings]
gtk-theme-name = MyGreybird
gtk-icon-theme-name = NoInherits
gtk-fallback-icon-theme = gnome  
```

Where **MyGreybird** is what has to be entered because my gtk theme is **~/.themes/MyGreybird** and **NoInherits** is my icon theme in **~/.icons/NoInherits**.

For reasons I don't fully understand, the full paths shouldn't be used. So, you'd replace **MyGreybird** and **NoInherits** with whatever your gtk and icon themes are called. Maybe a log out and log in will be needed to get the changes to take effect.

---

### Post by sudo san on 2013-10-07
> **vasa1 said:**
> Could you please provide the full path to the settings.ini file you created?

The applications you're having problems with, Synaptic & Software Center, are the ones that need "administrative privileges". See what you have in **/etc/gtk-3.0/settings.ini**.

Mine looks like this:
```
[Settings]
gtk-theme-name = MyGreybird
gtk-icon-theme-name = NoInherits
gtk-fallback-icon-theme = gnome  
```

Where **MyGreybird** is what has to be entered because my gtk theme is **~/.themes/MyGreybird** and **NoInherits** is my icon theme in **~/.icons/NoInherits**.

For reasons I don't fully understand, the full paths shouldn't be used. So, you'd replace **MyGreybird** and **NoInherits** with whatever your gtk and icon themes are called. Maybe a log out and log in will be needed to get the changes to take effect.

I can report that editing**/etc/gtk-3.0/settings.ini** successfully solved the problem on all applications that did not use the themes. This also worked on Audacious, but I forgot to mention it in the first post. This little fix is going into my openbox toolbox.

Thanks for all the help! :P

---

### Post by vasa1 on 2013-10-07
> **sudo san said:**
> I can report that editing */etc/gtk-**3**.0/settings.ini* successfully solved the problem on all applications that did not use the themes. This also worked on Audacious, but I forgot to mention it in the first post. This little fix is going into my openbox toolbox.

Thanks for all the help! :P Don't you mean **gtk-3.0**?
You are most welcome. People using the Openbox session in Lubuntu seem quite few (or quite silent). If you have some tips or advice, do share!

---

### Post by sudo san on 2013-10-10
> **vasa1 said:**
> Don't you mean **gtk-3.0**?
You are most welcome. People using the Openbox session in Lubuntu seem quite few (or quite silent). If you have some tips or advice, do share!

Ah, yes I did mean that and I will change that so others that may not get confused and can also be helped too!

---

