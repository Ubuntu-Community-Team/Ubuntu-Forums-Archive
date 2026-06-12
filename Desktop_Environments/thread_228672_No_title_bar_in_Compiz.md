---
title: "No title bar in Compiz?"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Tosa on 2006-08-03
Well, compiz is finally more or less functional on my Pc (Kubuntu, Radeon 9600XT). I sad more or less because there are no window borders and title bar. I can't do anything with windows. They are stuck where they show up!?

Another thing is that of all eye candy promised I've got only wobbling; and it so exaggerated that it renders menus almost useless. I've tried Gset-Compiz, but it doesn't have any effect on compiz behaviour.

So, how do I make my Windoze friends envious? :twisted:

---

### Post by Washington Irving on 2006-08-03
This might work:

> run gconf-editor:

Code:

gconf-editor


And navigate to /apps/compiz/general/allscreens/options/
and double-click on "active_plugins". Or right-click on active_plugins and 'Edit Key'.

Now add each of these values by clicking +Add
Please note that each of these values have to be in the correct order!

Code:

gconf decoration wobbly resize move minimize scale fade place cube rotate zoom switcher opacity



got this from [this HOWTO]("http://ubuntuforums.org/showthread.php?t=133427")

---

### Post by Tosa on 2006-08-03
Thanks!

  	 	 	 	 	 	 	 	  The order of plug-ins my script was a bit different, but nothing changed after rearranging them...

---

