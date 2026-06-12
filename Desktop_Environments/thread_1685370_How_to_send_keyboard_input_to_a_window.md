---
title: "How to send keyboard input to a window"
date: 2011-02-10
forum: Desktop Environments
---

### Post by fernandoc1 on 2011-02-10
I want to create a script to send input to an already open window from the command line.
The reason that I want to do this is to automatically control a game running on a emulator screen.
So, for example, I want to send commands like "up" "up" "w" "s" ...
Do someone have any idea on how can I do this?

---

### Post by Krytarik on 2011-02-10
You could use "xdotool" for that, in combination with "wmctrl", both are named as such in the official repos.

I use similar scripts to send keys to mplayer, to control fullscreen and mute. Actually I use "xsendkeycode" for that, but would I have to write them now, I would do it "xdotool", it's easier.

This is the one to control fullscreen, adapted to "xdotool":
```
#!/bin/sh

mplayerid=`xwininfo -name MPlayer |grep 'Window id:' |cut -d" " -f4`
if [ -n "$mplayerid" ]; then
wmctrl -i -a "$mplayerid"
else
wmctrl -a SMPlayer
fi
xdotool key f
```For "up" you have to use cap case: "Up".
You can lookup each keys "name" by running "xev" in a terminal, and then pressing the respective key.

If you know the exact name of the window and there is only one window containing the specified name, you can just use
```
wmctrl -a NAME
```like in the above example with SMPlayer.

---

### Post by fernandoc1 on 2011-02-14
Thanks for your response. It really works fine for me.

I've created a document with the script that I have done to control my game.

[https://docs.google.com/document/pub?id=17_OKZSl7gEaI9XZrkJqXa5UE0_ajoaSz_pYuBRv0Ugw]("https://docs.google.com/document/pub?id=17_OKZSl7gEaI9XZrkJqXa5UE0_ajoaSz_pYuBRv0Ugw")

Now, with this script, I can control a game running inside PCSX emulator.

---

### Post by Krytarik on 2011-02-14
I suppose you don't need the if/then conditions at all, I just had it in there because I switched between plain MPlayer and SMPlayer that time, I just now removed it as well, it's faster without the xwininfo query.

This should be sufficient for you:
```
#! /bin/bash
function Move {
               wmctrl -a PCSX;
               xdotool key "$1";
               sleep 0.05;
}
```
What does this actually?
```
while [ true ]
do
       Move Right
       Move Left
       Move Right
       Move Left
done
```

---

### Post by fernandoc1 on 2011-02-14
I can make my character play around the scene alone, with this code.
I will try your suggestions.

---

