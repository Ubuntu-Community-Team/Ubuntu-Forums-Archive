---
title: "acrobat reader problems"
date: 2006-02-14
forum: Desktop Environments
---

### Post by hollowhead on 2006-02-14
Hopefully someone can help me with this.  I downloaded the acrobat7 rpm to to my usbstick to install on my laptop which does not have internet access yet.  Converted rpm to deb using alien OK.  Installed using dkpg OK.  When I try to run it the splash appears then nothing happens.  Anyone know the solution to this?

Ta.

---

### Post by ESPOiG on 2006-02-14
conect it to internet... or if u have alien installed install it using alien and try that

sudo alien adobe_reader.rpm

other than that... i wuldnt have a clue get sumone that know more on wat they r talkin about :P

---

### Post by anirban.sam on 2006-02-14
try automatix, worked well for me

---

### Post by hollowhead on 2006-02-15
Thanks for the replies.  I have every intention of installing automatix but at the moment I have no internet access (seperate post) or wifi.  I tried reinstalling it.  No joy.  I'm going to download the rpm onto my usbstick again and try that in case its corrupted but I wondered later whether it might be a permissions thing.  Acrobat added an item to the gnome menu under the wp section.  If you click on this it comes yp with a message saying acroread can't run since there is no permission.  I added a launcher to the desktop runing the script found within the usr/share/acrobat7/.... subdirectories.  Maybe if the permissions are not right on /usr/bin/acroread it gets so far. Weird you'd have thought it would set up the permissions properly.  Inciendentally I'd stick with the gnome pdf viewer but it doesn't open all pdfs.  Some appear as blanks.  Thanks again,  Hollowhead.

---

### Post by art on 2006-02-15
did you try running from terminal, maybe it will spit out some errror messages, which might help

---

### Post by GrumpyBob on 2006-02-16
I have this issue as well - any solution?
Automatix doesn't work well for me - I think something to do with the firewall at work.
Robert

---

