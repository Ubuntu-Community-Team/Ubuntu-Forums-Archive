---
title: "Starting Unity on desktop 1?"
date: 2016-03-28
forum: Desktop Environments
---

### Post by ashley-a on 2016-03-28
Hello, All.

For a while, I've been trying to get a desktop environment on desktop 1 (ctrl+alt+f8). I've tried ```
startx -- :1
``` but I can't get an *actual *
desktop environment running on it.
Then i tried running ```
unity
``` from tty1. I had window maker running on desktop 0, and I got this output: ```
WARNING:  no DISPLAY variable set, setting it to :0
stop: Unknown job: unity-panel-service
start: Unknown job: unity-panel-service
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Error: Another window manager is already running on screen: 0
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core

```
This lead me to believe I could get unity running on display 1, by setting the display variable. I'm not brilliant with the linux terminal, and I couldn't figure out why:
[LIST=1]
[*]startx won't let me launch a desktop environment and
[*]I couldn't set a display variable with the unity command (I tried to get help with "unity -h", but to no avail)
[/LIST]

Any ideas on what to do?

Thanks in advance!

---

### Post by grahammechanical on 2016-03-28
Have you noticed that from tty1 to tty6 we get a Linux login but not on tty8 & onwards. That have something to do with this situation.

Regards.

---

### Post by ashley-a on 2016-03-28
> **grahammechanical said:**
> Have you noticed that from tty1 to tty6 we get a Linux login but not on tty8 & onwards. That have something to do with this situation.

Regards.

Thanks for the reply.
From what I have found, tty7 onwards is graphics. Tty6 and downwards is terminal shells. My question is this: How do I get graphics on tty8, tty9, etc.
I *can* do it by typing ```
startx -- :1
``` for tty8, and ```
startx -- :2
``` for tty9, etc. but I cannot get a desktop environment to show up. Only my unity desktop background and unity style desktop icons. No launcher, no title bar, no GNOME-like interface, no OpenBox-like right click function.
Does the fact that I use ```
sudo service LightDM start
``` instead of startx have something to do with it? Or maybe the fact that I boot to text, not graphics?

Thanks.

---

### Post by ashley-a on 2016-03-28
Brilliant! Just figured it out!

I cannot get it to launch with a desktop environment, but I can launch a window manager (openbox, i3, wmaker, etc).

Here is how:
[LIST=1]
[*]In a linux shell, in the home directory, type: ```
sudo nano ~/.xintrc
```
[*]In the nano screen, type exec (put the name of your window manager you want to access here). The code will look something like: ```
exec openbox
```
[*]Save the Nano document (ctrl+x, y, enter).
[*]Type my original, not-working code wich works now: ```
startx -- :1
```.
[*]Boom! You have a desktop on tty8 :)
[/LIST]

Note: if you want to get one on tty9, type ```
startx -- :2
```, and so on.

Hope this helps anyone with the same issue!

---

