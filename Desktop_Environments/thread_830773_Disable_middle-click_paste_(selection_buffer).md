---
title: "Disable middle-click paste (selection buffer)"
date: 2008-06-16
forum: Desktop Environments
---

### Post by randysparks on 2008-06-16
Does anybody know how to disable the middle-click paste function? I find myself sometimes miss-clicking, particularly when scrolling through a large document using the wheel. 

Note that I DON"T want to disable the middle-mouse button because it's useful in other situations. What I really need to do is disable the X selection buffer. 

I read elsewhere that some X session managers allow you to add a config option to turn off the selection buffer, but I can't find where that option is for gdm, and nor can I find where I should insert the option (/etc/gdm/gdm.conf?).

---

### Post by randysparks on 2008-06-16
I'm bumping this because I'm sure somebody has faced this annoyance :(

---

### Post by sayyeah on 2008-06-20
I also don't want to do tricks by simply mapping the middle button to something else. Is there any "real" way of disabling paste feature ?
All the documents I found is concerned with re-mapping the middle button in xorg.conf.

---

### Post by Viper666 on 2008-07-17
only solution i see is to disable the middle-mouse button but i'm sure you don't want that cause it's usefull sometimes but if u do...

```
sudo gedit /etc/X11/xorg.conf
```
and look after something simmilar to this...
```
[LIST]
[*]Section "InputDevice"
[*]Identifier "Generic Mouse"
[*]Driver "mouse"
[/LIST]
```
and add 
```
Option "ButtonMapping" "1 3 3"
``` 
this will make it do what the right button does (u can put any number from 1-9 but im sure over 3 will make it unusable).

if u already have a line 
```
Option "Emulate3Buttons" "true" 
```
then u can click both buttons (left&right) simultaneously to "emulate" the middle click

Anyways from what i know the middle click reads from a buffer what to do... (copy/paste) and there might be a way to disable that instead but i have no idea...:confused:

PS: after u do that save the file & restart the X server (CTRL+ALT+Backspace)

---

