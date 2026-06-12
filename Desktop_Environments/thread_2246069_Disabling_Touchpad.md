---
title: "Disabling Touchpad"
date: 2014-09-28
forum: Desktop Environments
---

### Post by Hesediel on 2014-09-28
Hi i have a notebook that i use for writing. The problem is that the accidental touchpad touching makes all difficult. I would like to disable it making a shourtcut 
The pc does not have a default combination for disabling. I would like for example to set   key   fn+1 and fn+2  for disable the touch pad. (and i dont know wich is the command for the fn key)
I founded those commands
```
synclient TouchpadOff=0
synclient TouchpadOff=1
```
Those codes works on terminal but it is not useful, i need a shortcut.
I read that it can be possible to disable the touchpad while typing, i founded this command
```
syndaemon -d -t
```
But it seems dos not work

---

### Post by Rex Bouwense on 2014-09-28
Here is the whole Community Help WIKI article.
[https://help.ubuntu.com/community/Lubuntu/Mouse#Touchpad_settings](https://help.ubuntu.com/community/Lubuntu/Mouse#Touchpad_settings)

---

### Post by MikeyXX on 2014-09-28
I ended up using Touchpad-Indicator. It works perfectly with my Bluetooth mouse turning off my Touchpad as soon as my bluetooth mouse kicks in.

[http://www.webupd8.org/2011/02/touchpad-indicator-now-automatically.html](http://www.webupd8.org/2011/02/touchpad-indicator-now-automatically.html)

This will work great for you, as you can choose a hotkey combo to turn on and off your touchpad...including if you are typing it'll turn it off and then you select how many seconds to turn it on again. Brilliant!


Mike

---

### Post by Hesediel on 2014-09-28
Ok touchpad indicator makes good the disable while typing. But the hotkey does not work. I need the shortcut because i want to disable and enable the touchpad without an external mouse.

---

### Post by mc4man on 2014-09-28
If you need to use Fn+something then search out if remapping is possible in linux. Here on my laptop  Fn+F6 toggles the  touchpad on & off so it's an already available function.

---

### Post by varunendra on 2014-09-29
Please take a look at this post for hotkey mapping : [http://ubuntuforums.org/showpost.php?p=12819607](http://ubuntuforums.org/showpost.php?p=12819607)

It is written in context of a different issue, but will give you an idea of what to do. You can either create a similar script suggested in it to enable/disable the touchpad with a single combination, or, skip to Part "B." of the post to directly bind a pair of hot keys/combos with the synclient commands.

If you want detailed help with the script approach, just let us know.

If you prefer the simpler approach of binding the hotkeys directly with the commands, you'll need to type the command -
```
synclient TouchpadOff=0
```
instead of "**/bin/bash /bin/wifitoggle.sh**" in **step 8** of **part "B."** of the post.

Repeat the steps 3 to 10 for binding a different hot-key with "synclient TouchpadOff=1" command. Obviously, the "Name" in step 5 should also change.

---

