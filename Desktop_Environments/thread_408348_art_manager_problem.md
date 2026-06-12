---
title: "art manager problem"
date: 2007-04-13
forum: Desktop Environments
---

### Post by Pimpmaggot on 2007-04-13
i have all the repositories enabled yet i cannot find the art manager anywere in synamtec package manager or anywere else, can someone tell me what might be wrong???

---

### Post by ComplexNumber on 2007-04-13
> **Pimpmaggot said:**
> i have all the repositories enabled yet i cannot find the art manager anywere in synamtec package manager or anywere else, can someone tell me what might be wrong???
what exactly do you mean or are referring to when you say "art manager"? 

do you mean the place where you can select themes? if so, you can find that in the main manu -> system -> preferences -> themes.

---

### Post by Pimpmaggot on 2007-04-13
when i say art manager i am reffering to the program that allows you to download all the wallpaper and themes that are available for gnome, the theme manager in prefrences is something diffrent, i just re installed ubuntu 6.6 on a new system i got and i cant find the art manager, ive never had a problem getting it before

---

### Post by ComplexNumber on 2007-04-13
> **Pimpmaggot said:**
> when i say art manager i am reffering to the program that allows you to download all the wallpaper and themes that are available for gnome, the theme manager in prefrences is something diffrent, i just re installed ubuntu 6.6 on a new system i got and i cant find the art manager, ive never had a problem getting it before
i suspected that too, but i wondered why you didn't mention wallpaper manager or something. i had a look on gnomefiles, but couldnt find it.

i've just had another look and found it. its [here]("http://gnomefiles.org/app.php/GNOME_Art"). i don't know if its in the dapper repos because i'm using edgy so i can't check for you. if its not there (do a search in synaptic for "art-gnome" in the description), you'll have to compile it yourself by doing the following:
-download the tarball, then extract it. 
-in the terminal, go to where you extracted it and type in the folllowing:
**./configure**

wait for the configure script to complete without errors

then type in **make**

again, wait for it to complete. then type in the following:
**sudo make install**

---

### Post by Pimpmaggot on 2007-04-15
thanks man, i was able to find it in synaptec searching for gnome-art, thats funny, same program ive used before just a diffrent name, thanks again

---

