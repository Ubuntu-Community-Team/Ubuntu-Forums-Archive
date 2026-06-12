---
title: "Compiz installed but freezes when i compiz --replace"
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by kerrymorgan1 on 2007-08-20
i installed my Nvidia 8600 drivers then,  installed Compiz fusion using 

[http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository#amd64](http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository#amd64)
when i alt+f2 and type in compiz --replace it freezes

everything went through fine what else could i do to get it going? any help will be appreciated

---

### Post by Chymera on 2007-08-21
any other abnormal things you notice? like missing window borders?
i recommend you reinstall compiz... 
if that doesnt do the trick try running it from a terminal window instead of alt+f2 and post the output. also you might want to try compiz --replace &

---

### Post by swidowski on 2007-08-22
all you should have to do is from a terminal type
compiz --replace & gtk-window-decorator --replace &

the reason you don't have the decorator is because you basically didn't reload it after you started compiz(that is my best guess as to why).  also if you want it to autostart just add it to sessions startup but put compiz --replace on a single entry and then gtk-window-decorator --replace on a seperate entry. let me know if this helps.

---

### Post by EclipseAgent on 2007-08-22
> **kerrymorgan1 said:**
> i installed my Nvidia 8600 drivers then,  installed Compiz fusion using 

[http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository#amd64](http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository#amd64)
when i alt+f2 and type in compiz --replace it freezes

everything went through fine what else could i do to get it going? any help will be appreciated

I had this same thing on my openSUSE box.. It wasn't how it was starting, it wasn't anything else really.. 
 
I had to delete the .compiz folder and start back over and it worked :o)

---

