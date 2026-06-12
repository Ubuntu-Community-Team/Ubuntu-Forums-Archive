---
title: "Mouse leaves screen (TV-Out) while gaming"
date: 2007-12-23
forum: Gaming &amp; Leisure
---

### Post by Kimm on 2007-12-23
When I'm playing online games ('ts what I play :P) my mouse has a tendency to leave the screen, causing the game to lock and me to loose control of my character. This makes it impossible to play...

I havnt tried any native Linux games btw, so this is under wine. And the game I have most problems with is Jedi Knight: Jedi Academy.

Is it possible to somehow completely lock the mouse to the game? so that it cant leave the screen? I have tried playing in windowed mode... but it makes no difference.

---

### Post by scraze on 2009-10-06
I apologize for the bump; although the above post is almost 2 years old, it still is one of the first search results for a mouse leaving the screen. In a dual screen setup this can be a real pain in the old behind when trying to play a game that doesn't grab the mouse quite well (perhaps caused by a broken dxgrab when playing through WINE).

There is a simple solution in the form of Jail, a small program that checks every millisecond to see if your cursor has left the current screen, and if so, simply moves it back. I found it on a [Gentoo documentation page](http://en.gentoo-wiki.com/wiki/X.Org/Dual_Monitors#Mouse_Jail:_How_to_lock_your_mouse_in_the_monitor): however, the version of Jail it links to doesn't work for me on Debian Squeeze, and I suspect the same is true for Ubuntu.

So here's a moderately tweaked version that works for me: [Jail](http://hoekje.org/src/Jail.tar.gz). I kept the original files in the tar (Jail.c, gpl.txt, JailSwitch.sh and Makefile)  but JailSwitch.sh didn't work for me.
Installing Jail is quite easy - in terminal, do:
```

mkdir ~/bin && cd ~/bin # optional, you can choose a different dir
wget http://hoekje.org/src/Jail.tar.gz
tar -xvzf Jail.tar.gz
make

```

You now have a runnable binary called Jail in ~/bin/; with a properly configured PATH you should be able to run this out of the blue (just run Jail), otherwise you'll need to call it by path (i.e. ~/bin/Jail or  cd ~/bin && ./Jail  - those are equivalent).

A small warning is appropriate here: Jail will keep your cursor in the screen you started it until you kill it. Killing Jail directly can be done by Ctrl-C in the terminal you started it in; additionally you can run pkill Jail from any terminal.

I've been able to play Red Alert 3 on a dual screen with Jail; it works great for me!
Hope it does the same for you.

---

### Post by mister_playboy on 2009-10-09
If it's about using WINE, it belongs in the WINE section.

---

