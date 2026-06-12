---
title: "Screen resolution..!"
date: 2008-06-11
forum: Desktop Environments
---

### Post by mike87 on 2008-06-11
I installed Ubuntu 8.04 LTS a couple of days ago.... my screen resolution is 1440 X 900 in windows Vista, but on ubuntu the highest on the list is 1280X1024. Ubuntu installed my graphic card after I installed the OS and My graphic card is Sapphere radeon HD3870 512mb. How can i have the highest resolution that my monitor supports? My display is a 19 inch wide screen hp.


And i don't know anything about the terminal in linux...

---

### Post by cocopuffz on 2008-06-11
try "gksudo displayconfig-gtk" in terminal. It will open up a gui that edits your xorg.conf file. Try "autodetect" so that it finds your monitor model. Make sure you select the "widescreen" radio button. It should give you a selection of supported monitors with a the resolution. Example "Plug & play 1440 x 900". click on that and apply. 
That should now give you the option for 1440x900 when you go to the display resolution app.

Good luck.

---

