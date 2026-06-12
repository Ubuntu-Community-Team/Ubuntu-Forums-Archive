---
title: "[SOLVED] fluxbox and screen"
date: 2008-06-27
forum: Desktop Environments
---

### Post by Inxsible on 2008-06-27
I currently have two menu entries in my fluxbox menu```
[exec] (rtorrent) {mrxvt -name "rTorrent" -e /usr/bin/rtorrent} <>
[exec] (cplay) {mrxvt -name "cplay" -wd /media/WD500/Music -e /usr/bin/cplay} <>
```I would now like to use those two with screen.

How would I put in the screen command, and still have the same behavior?

I tried ```
screen -S cplay cplay /media/WD500/Music
``` but that adds all my music in the playlist and starts playing. All I want is to start in that directory, so that I can choose what I want to play.

---

### Post by Inxsible on 2008-06-28
I also tried ```
mrxvt -name "cplay" -e cd /media/WD500/Music && screen cplay
```That puts me in the proper directory but doesn't start cplay in the screen. In short nothing after && works :(

---

### Post by Inxsible on 2008-06-28
Alright !!!

I got it myself. I used these commands in the menu file, in case anyone's curious enough ! ```
[exec] (rTorrent) {mrxvt -name "rTorrent" -e screen -S rtorrent rtorrent} <>
[exec] (cplay) {mrxvt -name "cplay" -wd /media/WD500/Music -e screen -S cplay cplay} <>
```I knew I had to keep playing with the commands :)

---

