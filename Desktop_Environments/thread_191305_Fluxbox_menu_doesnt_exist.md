---
title: "Fluxbox menu doesnt exist"
date: 2006-06-07
forum: Desktop Environments
---

### Post by bacsa81 on 2006-06-07
Hello!
I have upgraded from Breezy to Dapper, just installed fluxbox as well, because the new xfce got "too big and slow" for me. Everything went fine exept that there is no menu in fluxbox!
I went to the /etc/X11/fluxbox and there was a short help what should I put into my ~/.fluxbox/menu file, but there was no folder like this so I have created it and now I have some settings there, but none of my installed programs.
Is this a feautre or bug? ;) 
Is there any chance to use my heavily modified gnome menu under fluxbox?
Thanks! Have a nice day!
Csaba

---

### Post by echo $USER on 2006-06-07
You must have installed it through synaptec.  If you download the latest version from the fluxbox site, and install it, it will create all you menus for you.

---

### Post by Personatech on 2006-06-07
A quicker method is to launch a terminal and type

sudo fluxbox-generate_menu -is -ds

(I'm not sure it needs sudo but just in case it does I use it...)

It'll take a minute to build your menu but it seems pretty comprehensive.  You can edit the ~/.fluxbox/menu file afterwards to remove items you might not want in the menu.  This is a lot easier than recompiling Fluxbox, imho.

---

### Post by bacsa81 on 2006-06-07
I did install it via synaptic, and I tried the command: 
fluxbox-generate_menu -is -ds
But I got replied:
"csaba@csaba:~$ fluxbox-generate_menu -is -ds
bash: fluxbox-generate_menu: parancs nem található"
In english, the command doesn't exists :)
For flux with the tab key I get these results:
"csaba@csaba:~$ flux
fluxbare  fluxbox   fluxconf  fluxkeys  fluxmenu"
With search I could find the script fluxbox-generate_menu, it was in the /usr/share/doc/fluxbox I unzipped it and put it into the /usr/bin chmod it to be executable and now it runs! :) Asking for ImageMagick, I just installed it via synaptic and now everything runs smooth :)
Thanks for all!!
Csaba

---

### Post by Ramses de Norre on 2006-06-07
```
sudo gunzip /usr/share/doc/fluxbox/fluxbox-generate_menu.gz
/usr/share/doc/fluxbox/fluxbox-generate_menu

```
I don't know about the options, this worked for me (I needed to do a little tweaking but it gives you the basics).
Use vi .fluxbox/menu to edit to your likings.

---

