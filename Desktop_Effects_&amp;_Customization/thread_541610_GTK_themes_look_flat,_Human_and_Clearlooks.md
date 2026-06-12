---
title: "GTK themes look flat, Human and Clearlooks"
date: 2007-09-03
forum: Desktop Effects &amp; Customization
---

### Post by Kreuger on 2007-09-03
For some reason all my GTK themes look flat. I don't know what I did but it's made them all really ugly. I usually used Human although I know Clearlooks should look the same as they should have rounded buttons and everything but they dont. Please help.

[URL="http://img300.imageshack.us/img300/4441/themebadig3.png"]
Here[/URL] is a shot of it flat (currently the desktop)

And [here]("http://img383.imageshack.us/img383/921/200709022121041024x768ssw2.png") is the rounded version how it used to and should be (as on my laptop)

---

### Post by Kreuger on 2007-09-04
Anyone got any ideas? I tried comparing between the two computers I have all the same GTK programs and libraries installed.

---

### Post by ayoli on 2007-09-04
it look like you don't have the right gtk engine for your theme or the gtkrc file of your theme is messed up.
try to launch a gtk app from command line and post the output here. It should give ideas of what's goin wrong.

---

### Post by Kreuger on 2007-09-04
Ok I tried Synaptic. Hopefully this is what you want.
> kreuger@kreuger-desktop:~$ sudo /usr/sbin/synaptic
Password:

(synaptic:32233): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
kreuger@kreuger-desktop:~$ 

**EDIT:** I found another thread that had the similar problem and so I went looking for the modules and copied them into the right place than removed everything related to gtk themes, reinstalled the ubuntulooks one and it fixed it! Or at least clearlooks is rounded again. Human looks like it's gtk1. Is there anyway I can just change the blue in clearlooks?

---

### Post by ayoli on 2007-09-05
On feisty, if your theme support it you can customize colors via the theme chooser (menu system>preferences>themes). Hit the second button on the right (should be called customize or something like that in english, I m not sure mine is in french), then choose the colors tab.
Another way is to download a clearlooks theme that suit your needs on [http://gnome-look.org](http://gnome-look.org)

---

