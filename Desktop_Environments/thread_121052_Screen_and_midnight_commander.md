---
title: "Screen and midnight commander"
date: 2006-01-24
forum: Desktop Environments
---

### Post by rustikus on 2006-01-24
Hi,

i have installed screen, mc and several other programs for the console.
Here is my .screenrc

```

shell   bash

screen -M -t root  0 su -
screen    -t emacs 1 emacs-snapshot -nw
#screen    -t "esddsp mp3blaster" 2 mp3blaster -l music.lst
screen    -t mp3blaster 2 mp3blaster -l music.lst
screen    -t bash 3
screen    -t mc 4 mc

select 3

```

But i have a little problem to get mc to work in screen. I have set up mc to launch external programs for several types of files, i.e when i select an pdf file the viewer evince should be started. Here is the problem, when i start mc in an own terminal everything works fine, but when i start mc in screen i could not launch any program from mc. Is there a way to get mc to work in screen?

Thanks.

---

### Post by awi on 2006-01-25
X Window applications need the DISPLAY variable, you need to export that to the right value, you could get the value from your working terminal like this:

```
$ echo $DISPLAY

```
it should print something like this

```
:0
```

or 

```
localhost:0

```
Check the same variable inside your screen.

You might also need to allow other clients to connect to your X Server, to do that check for the [COLOR="DarkOliveGreen"]xhost [/COLOR]command.

---

