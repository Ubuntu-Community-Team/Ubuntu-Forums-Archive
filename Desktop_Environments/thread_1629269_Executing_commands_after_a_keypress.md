---
title: "Executing commands after a keypress"
date: 2010-11-23
forum: Desktop Environments
---

### Post by Mega-X on 2010-11-23
Hi guyz. :D

My question is the following: I want to execute some commands after I press some key but I really cannot figure out how to get the input from the keyboard.

Note that I don't want to get the input from the shell but, more generally, I want to control the keyboard input whenever I am.

I think that it should be something like a big case-esac statement with all the keys that I want but, again, how can I get the input from the keyboard?:confused:

---

### Post by Mega-X on 2010-11-26
uppppppppppppppp

---

### Post by tom4everitt on 2010-11-27
What you want is some way of getting the *key events* to affect your bash script. The 'xev' command gives you information about all key events, but is perhaps not usable in a bash script. 

I found this on a quick googling:
[http://www.astahost.com/info.php/Hotkeys-Keyboard-Quick-Launch-Keys-Linux_t1813.html](http://www.astahost.com/info.php/Hotkeys-Keyboard-Quick-Launch-Keys-Linux_t1813.html)

where something called called xbindkey is suggested. It is supposed to connect key events to bash commands. I haven't looked into it more closely, but hopefully it's the way to go. 

Good luck

---

### Post by Mega-X on 2010-11-27
> **tom4everitt said:**
>  [...] xbindkey is suggested. It is supposed to connect key events to bash commands. I haven't looked into it more closely, but hopefully it's the way to go. 

Good luck

It works, BUT it doesn't in UT99. I wanted to do some kind of script that makes the dodge movement without double clicking the movement key by setting something like:

"xdotool key <movement key>; sleep <delay in seconds between the first and second keystroke>; xdotool key <movement key>"
<key that you want>

The problem of this thread is solved, so I'm going to pre-append to the title of the thread the word "[SOLVED]", but I'm also going to open a new Thread in the "Gaming & Leisure" category because I want to solve the problem on UT99; however thank you for helping me. :wink:

---

### Post by tom4everitt on 2010-11-27
Aah, too bad it didn't work out. Perhaps UT99 catches all key events, without transmitting them to Gnome or whatever. For example that happens to me all the time when I'm watching a flash video in my browser and try to close the window with ctrl+w: it doesn't work. Presumably because flash, when in focus, is grabbing all key events before Gnome.

---

### Post by Mega-X on 2010-11-27
> **tom4everitt said:**
> Aah, too bad it didn't work out. Perhaps UT99 catches all key events, without transmitting them to Gnome or whatever. For example that happens to me all the time when I'm watching a flash video in my browser and try to close the window with ctrl+w: it doesn't work. Presumably because flash, when in focus, is grabbing all key events before Gnome.

Wow, then a new question arises: how can I catch the events from Gnome? :P

---

### Post by tom4everitt on 2010-11-28
In my head at least, that was the question you just solved with xbindkeys. But perhaps it is not really Gnome but X or the kernel you are catching the events from. I know too little about this to be sure. 

If I understood you correctly, it was working fine with xbindkeys when in your desktop (Gnome). But when you entered your game, the commands were not executed anymore. I think it would be the same if you watched a flash video in the browser.

---

