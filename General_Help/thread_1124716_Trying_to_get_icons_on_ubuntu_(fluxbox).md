---
title: "Trying to get icons on ubuntu (fluxbox)"
date: 2009-04-13
forum: General Help
---

### Post by devin0 on 2009-04-13
Hello, i have been messing around with ubuntu server for a few days now and need some help. I have just installed fluxbox, but there are no desktop icons. I belive i need to set up idesk to get the desktop icons to appear but am unsure how to set it up. Can someone please help me with this or give a link to a good toutorial for this? Thanks.

---

### Post by kerry_s on 2009-04-13
there are several ways to get desktop icons.

idesk is a little tricky.
rox-filer and pcmanfm is easier, for rox you just add "rox -p=Default" to your startup. pcmanfm you just select manage desktop then add "pcmanfm" to the startup.

with rox and pcmanfm you can just drag and drop the applications from /usr/share/applications right on the desktop.
with rox you can also use executables from /usr/bin or make your own, plus rox lets you set keyboard short cuts directly to the icon.

rox is the best. ;) takes seconds to set up. i'll do it real quick.

---

### Post by kerry_s on 2009-04-13
sorry the uploads slow and it's converting all my png's to jpg's.
the last pic, it only lets you put 5 at a time.

---

### Post by devin0 on 2009-04-13
Hey thanks for all the info I just figured out how to use idesk but im going to try rox and pcmanfm next.

---

### Post by devin0 on 2009-04-13
I just took a look at rox and pcmanfm and like you said they are much easire to use compared to idesk. Can you tell me how to add them to my startup?

---

### Post by kerry_s on 2009-04-13
you just put them it in your ~/.fluxbox/startup file

for rox:
rox -p=Default &

for pcmanfm:
pcmanfm --daemon &

[http://fluxbox-wiki.org/index.php?title=Howto_edit_the_startup_file](http://fluxbox-wiki.org/index.php?title=Howto_edit_the_startup_file)

---

