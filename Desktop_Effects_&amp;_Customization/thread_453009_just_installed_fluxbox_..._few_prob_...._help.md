---
title: "just installed fluxbox ... few prob .... help"
date: 2007-05-23
forum: Desktop Effects &amp; Customization
---

### Post by vilto on 2007-05-23
hi guyz i just installed fluxbox 
i have few issues im facing with it 
1)i installed conky too but when i start there is a prob look at the file uploaded ....  there is a green backgreound coming up............................. it works fine in gnome
2)when i right click and pressed exit only flux box is exitting and rox and other app lications i opened still remains thr so i had to press ctrl+alt+backspace to go to GDM ....... so how can i make it such that by clicking on exit it goes to the GDM

i have gnome and kde too installed and im loging into fluxbox from GDM........

---

### Post by vilto on 2007-05-23
one more thing as u can see my conky is not detecting my hardware temperature how to do it?........ its the same case in gnome too ............

---

### Post by kerry_s on 2007-05-23
Maybe it's your conky settings? can you post your .conkyrc?
also do you got all the compatibility settings checked in rox?
Also do you have gdm background color set to black? ( gksu gdmsetup )
also try running> fbsetroot -solid black

conky temp setting> Temp: ${acpitemp}C

---

### Post by vilto on 2007-05-24
im attaching my conky file as i said its working fine in gnome
yes i got all compatible conditions clicked in rox
im using a themed gdm
when i try fbsetroot -solid black this im getting some error
                
                 Warning: Failed to open file(/usr/share/fluxbox/nls/en_IN.UTF-8/fluxbox.cat)
                for translation, using default messages.

---

### Post by kerry_s on 2007-05-24
Okay on line 51 you have>  default_color green
that's most likely why you got green background.

```
Warning: Failed to open file(/usr/share/fluxbox/nls/en_IN.UTF-8/fluxbox.cat)
for translation, using default messages.
```

That's a normal error, if you want to fix it use this->

sudo ln -s /usr/share/fluxbox/nls/C /usr/share/fluxbox/nls/en_IN.UTF-8

---

### Post by vilto on 2007-06-01
no the default color green means the text color is green not the background.............. as i told it is fine in gnome

---

