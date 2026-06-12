---
title: "GIMPshop"
date: 2006-01-30
forum: Desktop Environments
---

### Post by ESPOiG on 2006-01-30
anyone else wanna know how to install GIMPshop in Ubuntu, cuz i really wuld like to and since im not really a LINUX guru i have no idea. cuz it is just in RPM format at the moment, well it was last time i look

i wuld grtly appriciate any help anyone can give me, and im sure others will as well

---

### Post by leech on 2006-01-30
[http://ubuntuforums.org/showthread.php?t=67525](http://ubuntuforums.org/showthread.php?t=67525)

There you go.

Leech

---

### Post by ESPOiG on 2006-01-30
how exactly do i install a .deb file ??? that i have downloaded eg. gimpshop.deb

:D im new to linux and debian altogether

---

### Post by mustang on 2006-01-30
[QUOTE=ESPOiG]how exactly do i install a .deb file ??? that i have downloaded eg. gimpshop.deb

:D im new to linux and debian altogether[/QUOTE]

```
sudo dpkg -i *filename.deb*
```

---

### Post by ESPOiG on 2006-01-30
how do i direct the terminal command to the specific folder the .deb file is in

wen i do this

sudo dpkg -i /home/ross/documents/downloads/gimp-2.2.8_2.2.8-1_i386.deb

it says it cannot access the file or it does not exist, so then i just pasted it in my home directory and that worked fine cuz i didnt have to redirect it

---

### Post by mustang on 2006-01-30
[QUOTE=ESPOiG]how do i direct the terminal command to the specific folder the .deb file is in

wen i do this

sudo dpkg -i /home/ross/documents/downloads/gimp-2.2.8_2.2.8-1_i386.deb

it says it cannot access the file or it does not exist, so then i just pasted it in my home directory and that worked fine cuz i didnt have to redirect it[/QUOTE]

That means "/home/ross/documents/downloads/" is not the right directory. Try this

type "sudo dpkg -i /h" and then hit tab. Notice how it autocompletes the directory for you. Use this trick so that you can point dpkg to the right directory.

---

### Post by ESPOiG on 2006-01-30
k i did that but im not entirelly sure how that helps me cuz i pressed tab and it just brings up home :D.... so now i have sudo dpkg -i /home

can u explain it a bit more plz

---

### Post by BLTicklemonster on 2006-01-30
[QUOTE=ESPOiG]how exactly do i install a .deb file ??? that i have downloaded eg. gimpshop.deb

:D im new to linux and debian altogether[/QUOTE]
Here's a neat trick to run .deb files with a double click: [http://www.ubuntuforums.org/showthread.php?t=114215](http://www.ubuntuforums.org/showthread.php?t=114215)

Pass this along, it's a good one!

---

### Post by ESPOiG on 2006-01-30
tis ok now i figured it out... u hvae to put caps on the front of the directories :P

not documents // Documents

---

