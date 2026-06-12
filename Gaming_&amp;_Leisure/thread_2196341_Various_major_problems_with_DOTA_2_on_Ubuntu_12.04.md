---
title: "Various major problems with DOTA 2 on Ubuntu 12.04/Unity"
date: 2013-12-29
forum: Gaming &amp; Leisure
---

### Post by Zorgoth on 2013-12-29
I have been playing the native linux version of DOTA 2 and have several serious problems. Here they are in order of severity:

1) When the game crashes in fullscreen (which is frequent), and I switch to a tty to kill it (which requires extreme prejudice, otherwise the game does not close), the image of the game remains on the screen and absolutely nothing can be done with the computer except move the mouse or switch to a tty, forcing me to restart the computer.
2) When I alt-tab or switch desktops while the game is in fullscreen mode, the game often crashes (moving to step 1 and making me restart the computer)
3) Frequently while playing, something happens (I don't know what) which causes the (fullscreen) app to lose focus, pushing the dock above the game (however, I cannot actually use the dock *or* the game effectively when this happens - I can switch desktops and select the game to get it back to normal, but it wastes about 10 or 20 seconds)

The obvious solution would be to use the borderless window, but afaik there is no way to make that go over the dock, which makes it useless.

Are there any fixes or workarounds for these problems, and are any of them things I should report to either DOTA 2 or Unity?

EDIT: I'm running it on a laptop with NVIDIA GT635M and bumblebee.

---

### Post by dannyboy79 on 2013-12-29
is it possible for you to edit the properties of your dock and make it so it does NOT always stay on top so that at least you can play in windowed mode? also, i have noticed that when I have to kill an app from a tty, sometimes there are multiple instances running, when you kill it what command are you using? ```
sudo killall dota2
``` (OR whatever dota2 runs as) instead of using ```
sudo kill processID
```
i can't suggest anything other than that as I don't play DOTA2, good luck

---

