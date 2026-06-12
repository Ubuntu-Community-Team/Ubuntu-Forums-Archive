---
title: "what was the command to config x?"
date: 2006-01-19
forum: General Help
---

### Post by taseal on 2006-01-19
I am trying to set linux back up on my desktop, but I keep getting the error 'no screen found' I remember I got rid of this problem once I configured x.....

what was the command for it? I thought it was sudo config x I guess not

anyone know?

---

### Post by BateauSurLEau on 2006-01-19
I do believe it was 'sudo dpkg-reconfigure -phigh xserver-xorg'

---

### Post by ardchoille on 2006-01-19
[QUOTE=taseal]I am trying to set linux back up on my desktop, but I keep getting the error 'no screen found' I remember I got rid of this problem once I configured x.....

what was the command for it? I thought it was sudo config x I guess not

anyone know?[/QUOTE]
sudo dpkg-reconfigure xserver-xorg

---

### Post by taseal on 2006-01-19
[QUOTE=ardchoille]sudo dpkg-reconfigure xserver-xorg[/QUOTE]

ugh it didnt work!

it keeps saying fatal server error: no screens found :( upon opening the file it tells me to open for further info the error seems

The directory /usr/share/X11/fonts/cyrillic does not exist
The directry /usr/share/x11/fonts/CID does not exist

i'm not sure what that has to do with the error no screens found but...

---

### Post by dcstar on 2006-01-19
[QUOTE=taseal]ugh it didnt work!

it keeps saying fatal server error: no screens found :( upon opening the file it tells me to open for further info the error seems

The directory /usr/share/X11/fonts/cyrillic does not exist
The directry /usr/share/x11/fonts/CID does not exist

i'm not sure what that has to do with the error no screens found but...[/QUOTE]
Those messages are irrelevant, ignore them.

What video card are you selecting?

---

### Post by taseal on 2006-01-19
[QUOTE=dcstar]Those messages are irrelevant, ignore them.

What video card are you selecting?[/QUOTE]


well I do autodetect and it picks out the right card which is an ATI x700

---

### Post by taseal on 2006-01-19
anyone, please help :(

---

### Post by adam.tropics on 2006-01-19
Try selecting Vesa (driver) just to see if you can get X at all! It normally works fairly universally on ATI stuff. Then search the forums for the ATI how to guides, there are a couple!

---

### Post by taseal on 2006-01-20
i'll try that...

i dont see why it doesnt work :( it worked before :(

---

