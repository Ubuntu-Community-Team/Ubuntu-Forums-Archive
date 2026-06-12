---
title: "Screenshot while playing"
date: 2009-11-22
forum: Gaming &amp; Leisure
---

### Post by 569874123 on 2009-11-22
Howdy :)
Is it possible to take a screenshot while playing? How?
Thanks.

---

### Post by Vadi on 2009-11-22
Most games often have built-in screenshot abilities. Otherwise, just alt+tab, and take a screenshot with a delay?

Shutter has delay: [http://shutter-project.org/](http://shutter-project.org/)

---

### Post by 569874123 on 2009-11-22
> **Vadi said:**
> Most games often have built-in screenshot abilities. Otherwise, just alt+tab, and take a screenshot with a delay?

Shutter has delay: [http://shutter-project.org/](http://shutter-project.org/)

I cannot alt-tab out of grid wars 2.

---

### Post by rettichschnidi on 2009-11-22
I have a small script: 

```
while true
do
	nice -n 20 import -window $1 "$2-`date +%H%M%S`.jpg"
	sleep 10
done
```

For screenshots of a windowed game: start "xwininfo" and select the window -> gives you a window id like "0x581fcb7"

```
scriptname.sh 0x581fcb7 gamename
```
For screenshots of a fullscreen game: 
```

scriptname.sh root gamename 
```

---

### Post by 569874123 on 2009-11-23
> **rettichschnidi said:**
> I have a small script: 

```
while true
do
	nice -n 20 import -window $1 "$2-`date +%H%M%S`.jpg"
	sleep 10
done
```

For screenshots of a windowed game: start "xwininfo" and select the window -> gives you a window id like "0x581fcb7"

```
scriptname.sh 0x581fcb7 gamename
```
For screenshots of a fullscreen game: 
```

scriptname.sh root gamename 
```
Can you modify that script to take a screen shot when i press a button while in full-screen mode in a game? Thank you.

---

### Post by akoskm on 2009-11-23
> **569874123 said:**
> I cannot alt-tab out of grid wars 2.

You don't need to alt-tab from the game. I think you have a button like PrintScreen, press that one.
If the game have some built-in function for taking screenshots, then set the window-managers screenshot hotkey (System > Preferences > Keyboard Shortcuts) to something else than PrintScreen, example: SHIFT+PrintScreen. Restart the window-manager and now you can use the PrintScreen button in the game.

---

### Post by 569874123 on 2009-11-23
> **akoskm said:**
> You don't need to alt-tab from the game. I think you have a button like PrintScreen, press that one.
If the game have some built-in function for taking screenshots, then set the window-managers screenshot hotkey (System > Preferences > Keyboard Shortcuts) to something else than PrintScreen, example: SHIFT+PrintScreen. Restart the window-manager and now you can use the PrintScreen button in the game.

PrintScreen doesn't work while playing games.

---

### Post by kostkon on 2009-11-23
Try *glc*.

---

