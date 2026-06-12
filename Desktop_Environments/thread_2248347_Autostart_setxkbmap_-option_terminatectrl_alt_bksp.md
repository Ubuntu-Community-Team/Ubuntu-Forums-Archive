---
title: "Autostart setxkbmap -option terminate:ctrl_alt_bksp"
date: 2014-10-14
forum: Desktop Environments
---

### Post by kalsan on 2014-10-14
Hi there!
I want to be able to kill XFCE when it freeses using Ctrl+Alt+Bksp. I figured that the command setxkbmap -option terminate:ctrl_alt_bksp would do that. Unfortunately, the command has no effect if I put it into autostart.
So I made a SH script and pasted the command there, putting the script into autostart. Still doesn't work. I suppose this has to do with the user groups.
How do I permanently enable Ctrl+Alt+Backspace on XFCE?
Cheers,
Kalsan

---

### Post by Toz on 2014-10-14
I find that running an Xfce autostart command in a bash -c "" wrapper command seems to work better. Try:
```
bash -c "setxkbmap -option terminate:ctrl_alt_bksp"
```
...as your autostart command.

If that still doesn't work, you may want to try introducing a pause at the beginning (in case something else in the regular startup is overwritting your command). In that case, try:
```
bash -c "sleep 2s && setxkbmap -option terminate:ctrl_alt_bksp"
```
...and adjust the 2s to suit.

---

