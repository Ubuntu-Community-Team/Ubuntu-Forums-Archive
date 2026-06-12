---
title: "xmodmap does only half the job"
date: 2013-10-08
forum: Desktop Environments
---

### Post by richardhwinter on 2013-10-08
**Ubuntu 12.04**
**The situation**
I bought a Lenovo T420. It has the normal German keyboard layout but unfortunately it has a larger shift key and the greater / less key is missing. Doing a lot of html this was a catastrophe.
**First Steps to a solution**
I did some research and tried to understand the inner workings of xmodmap with the help of xev. With this I managed to get the - otherwise not used - menu key assigned to '<' and '>'. 
**The missing step**
Whatever I tried I didn't get the bar and broken bar part working. I'm running out of ideas and hope someone can guide me.
**Settings**
My attempt to change the key was:
```
$ xmodmap -e "keycode 135 = less greater less greater bar brokenbar"
$ xmodmap -pke >~/.Xmodmap
```
Checking with xev shows:
```
$ xev | grep keycode
    state 0x0, keycode 36 (keysym 0xff0d, Return), same_screen YES,
    state 0x0, keycode 135 (keysym 0x3c, less), same_screen YES,
    XKeysymToKeycode returns keycode: 94
    state 0x0, keycode 135 (keysym 0x3c, less), same_screen YES,
    XKeysymToKeycode returns keycode: 94

```
And when I read the map:
```
$ xmodmap -pke > /home/richard/Desktop/mykeyboard.txt
```
... it shows the following entries for keycode 135 and 94 (have to admit that I don't understand the "XKeysymToKeycode returns keycode: 94" part):
> keycode 135 = less greater less greater bar brokenbar
keycode  94 = less greater less greater bar brokenbar


Thanks for your help
Richard

---

