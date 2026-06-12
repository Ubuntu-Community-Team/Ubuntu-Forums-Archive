---
title: "Messed up Compiz/Graphics setup"
date: 2009-09-04
forum: Desktop Environments
---

### Post by celticbhoy on 2009-09-04
I need a little help with my Compiz setup. I am running an Acer Aspire One which has onboard Intel graphics using Jaunty all up to date. Compiz did work without any problems until about a week ago, I had the netbookm connected to a TV for watching some sport and suddenly I got a white screen with only the mouse showing. I have tried uninstalling and re-installing, and even to remove as many config files as I can find, but every time I start Compiz I get the same white screen.


Any help!

---

### Post by andrea000 on 2009-09-05
Does it give any errors?Have you tried running compiz
in the terminal maybe that will point you to what the
problem is.

---

### Post by owise1 on 2009-09-05
Try resetting xorg - I has a probelm with compiz after connecting to an external monitor - set virtual reolution too high.

run following in a terminal

sudo dpkg-reconfigure xserver-xorg

then log out log in

---

### Post by celticbhoy on 2009-09-05
Thanx, that worked.

---

