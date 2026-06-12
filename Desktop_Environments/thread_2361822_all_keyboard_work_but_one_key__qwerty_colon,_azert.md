---
title: "all keyboard work but one key : qwerty colon, azerty semi-colon ;"
date: 2017-05-21
forum: Desktop Environments
---

### Post by millicent-billette on 2017-05-21
It look to be the same problem than describe here : [https://ubuntuforums.org/showthread.php?t=888097](https://ubuntuforums.org/showthread.php?t=888097)
It's not an hardware failure.
It's work in Ctrl+Alt+F1 TTY, but not in Unity WM.
In the WM (window manager), qwerty "," colon key dont work nor by using physical keyboard, on screen virtual keyboard or thru teamviewer. But it work if i copy past it, or switch to TTY to type it outside of the window manager.

In azerty layout, it the same placed key that not working. ";" semi-colon. And Shift+";" is working resulting in "." on azerty layout.
I really don't understand the possible origin of this bug.
We are in 2017, the exact same bug look to have been describe in 2008

i've tested this : 
```
sudo dpkg-reconfigure console-data
```
based on this [https://askubuntu.com/questions/69306/tilde-and-double-quote-keys-dont-work-on-the-command-line](https://askubuntu.com/questions/69306/tilde-and-double-quote-keys-dont-work-on-the-command-line)
but it don't change anything.

Any clue ?

It's on a basic ubuntu 16.04 installation with few installed programs and few config change.
I've run
```

sudo apt-get update
sudo apt-get upgrade

```
and no change.

---

