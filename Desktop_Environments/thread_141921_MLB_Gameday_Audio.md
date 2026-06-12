---
title: "MLB Gameday Audio"
date: 2006-03-09
forum: Desktop Environments
---

### Post by brooklynlou on 2006-03-09
Greetings,

Anyone manage to get MLB gameday audio working with Ubuntu? If possible, please share the steps, thanks.

---

### Post by rcjhawk on 2007-06-29
> **brooklynlou said:**
> Greetings,

Anyone manage to get MLB gameday audio working with Ubuntu? If possible, please share the steps, thanks.

Sheesh, no replies after all this time?

There are several sites that claim solutions:

[http://www.geekandproud.net/archives/2007/03/23/1045/mlbtv-on-linux/](http://www.geekandproud.net/archives/2007/03/23/1045/mlbtv-on-linux/)

[http://people.iarc.uaf.edu/~cswingle/baseball/mlb_linux.php](http://people.iarc.uaf.edu/~cswingle/baseball/mlb_linux.php)

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

or do what I do: :(

1) Bring up Gameday for the game you want

2) Click on "Listen Live on Gameday Audio"

3) Pick your station (you may have to click the Listen button on the right) [popups have to be enabled to see this page]

4) View the source for the frame with the MLB.com logo

5) Search for the address that starts "http://web.servicebureau.net/"

6) Copy that string to the X11 clipboard (i.e., highlight it)

7) Open a terminal window

8) On the command line, run

xine "http://web.servicebureau.net/xxxxxxxx" &

where xxxxx is the rest of the string in 5)

9) Listen

Lacks a certain elegance, and you can't easily switch between games, but it works ;)

---

### Post by NoVista on 2007-06-30
Both the audio and the video work fine in Feisty.

Look Here:

[http://ubuntuforums.org/showthread.php?t=385277](http://ubuntuforums.org/showthread.php?t=385277)

---

