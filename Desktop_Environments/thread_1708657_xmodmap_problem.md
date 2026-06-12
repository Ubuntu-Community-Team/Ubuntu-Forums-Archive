---
title: "xmodmap problem"
date: 2011-03-17
forum: Desktop Environments
---

### Post by Zucriy Amsuna on 2011-03-17
I have a funky keyboard on this laptop; the right shift key is annoyingly small... The Menu key is taking up its space. So I first used xmodmap to make the useless Alt Gr key to Menu:

```
xmodmap -e "keycode 108=Menu"
```Success. And then when I try to change the Menu key to its neighbour:

```
xmodmap -e "keycode 135=Shift_R"
```It doesn't work. According to the xev command, the key is mapped to Shift_R. but it doesn't act like it. I tried mapping it to other keyboard actions, and they work; both Shifts don't seem to work, though. The only difference between them in xev's display, besides their individual keycodes, is the following line for the problem key (Menu):

```
XKeysymToKeycode returns keycode: 62
```62 is the keycode for Shift_R. Why does it do this? Does it matter? And how can I make it work?

(And, as extra info, the OS is Linux Mint with a Bash terminal.)

---

### Post by Krytarik on 2011-03-17
> **Zucriy Amsuna said:**
> 
```
XKeysymToKeycode returns keycode: 62
```62 is the keycode for Shift_R. Why does it do this? Does it matter?
First, this of course states "keycode 62", because the key is mapped to those keycode. So, that is correct, and expected.

After oscilliating between fiddling around and studying the manual I eventually managed it and I'm quite happy to be able to present a solution! Because of the special feature of "Shift_R" to be a modifier, you have to run a number of commands to add "Menu" to the modifier.

When the "Menu" key is mapped normally, those commands will be sufficient:
```
xmodmap -e "remove Shift = Shift_R"
xmodmap -e "keysym Menu = Shift_R"
xmodmap -e "add Shift = Shift_R"

```That was fun! :)

Greatings.

---

### Post by Zucriy Amsuna on 2011-03-19
Thank you. ^_^ I'm glad it was fun.

---

