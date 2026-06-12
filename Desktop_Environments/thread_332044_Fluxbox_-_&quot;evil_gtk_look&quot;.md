---
title: "Fluxbox - &quot;evil gtk look&quot;"
date: 2007-01-05
forum: Desktop Environments
---

### Post by Kulgan on 2007-01-05
I've been trying out fluxbox for the last few days - and love it for the easy config!

I got themes and the like going, installed artwiz fonts succesfully (how could I not, when they are in the repos...) and generally had fun with startup and menu files :D

The next step would be to change the grey theme-less "old GTK" look that is plaguing all the windows... Would someone mind sharing how to? And what to replace it with ? :D

Never felt such a noob before :-k 

Cheers
-K

---

### Post by K.Mandla on 2007-01-05
I think if you poke around in the repositories, you should find some straight gtk themes that aren't so god-awful ugly. If you install *gtk-theme-switch* and enter the command

```
switch
```
you'll get a primitive little dialog that lets you try them out, and switch if you like.

---

### Post by Kulgan on 2007-01-05
I see... so fluxbox uses the same as gnome would.. or at least sort of? Awesome :D

Thanks, I'll give it a try...
but wouldn't it be switch2, for GTK2?

-K

---

### Post by RedSquirrel on 2007-01-05
> **Kulgan said:**
> I see... so fluxbox uses the same as gnome would.. or at least sort of? Awesome :D

Thanks, I'll give it a try...
but wouldn't it be switch2, for GTK2?

-K

Hmm...

I don't use switch at all.

I simply created the file ~/.gtkrc-2.0 in which I put the following (for IndustrialTango):

gtk-icon-theme-name = "Tango"
gtk-theme-name = "IndustrialTango"
gtk-font-name = "Sans 10"

Works fine, but I may have a look at that switch at some point....

---

### Post by jem7v on 2007-01-06
switch2 is in the same package (gtk-theme-switch) and yes, it's the one you should use for GTK2 themes. switch is for GTK1

---

### Post by K.Mandla on 2007-01-06
> **Kulgan said:**
> but wouldn't it be switch2, for GTK2?
Yeah, switch2. When you said "old GTK" I thought you meant straight GTK. :rolleyes:

---

### Post by fuscia on 2007-01-06
this is what you want - [http://plasmasturm.org/code/gtk-chtheme/](http://plasmasturm.org/code/gtk-chtheme/)

had the same problem with openbox - [http://ubuntuforums.org/showthread.php?t=265921](http://ubuntuforums.org/showthread.php?t=265921)

---

### Post by K.Mandla on 2007-01-06
> **fuscia said:**
> this is what you want - [http://plasmasturm.org/code/gtk-chtheme/](http://plasmasturm.org/code/gtk-chtheme/)
Ooh! A new toy! :D

---

### Post by Kulgan on 2007-01-06
thanks, all

fiddled around for a while to find a theme that matches the fluxbox theme I have, but it looks much better now!

ta

gtk-chtheme looks like it has a better previewing method... I will definitely have fun with this 'toy' :p

---

### Post by Ramses de Norre on 2007-01-06
I just put gnome-settings-daemon in my startup file.. But it might not be what you want.

---

### Post by Kulgan on 2007-01-06
it seems to be working fine now, even with reboots... the only thing now is that the terminal that is "pasted" to the desktop appears on the toolbar... which it didn't do before :-k

---

