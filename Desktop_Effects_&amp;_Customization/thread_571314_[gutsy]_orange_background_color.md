---
title: "[gutsy] orange background color"
date: 2007-10-09
forum: Desktop Effects &amp; Customization
---

### Post by rysh on 2007-10-09
I change my desktop color but when i login there is still this orange color from the default settings. I already also changed this in the gdm theme ... but it seems it doesn't have the effect i want still an orange background is shown before gnome actually starts ... is this orange color somehow compiled into the binaries ? 

How to get rid of it? ...

---

### Post by Forlong on 2007-10-09
You're right, that seems to be a bug in Gutsy.

Here's how you can change it manually:
```
sudo gedit /etc/gdm/PreSession/Default
```
Then look for
```
	# Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="#dab082"
```
And change the hexadecimal code to whichever you like.
E.g. for black #000000 and white #FFFFFF

---

### Post by rysh on 2007-10-09
Indeed indeed, thank you very much.

---

### Post by LinuxIsInnovation on 2007-12-18
Thanks dude.. I like orange but this is better!! :D

---

