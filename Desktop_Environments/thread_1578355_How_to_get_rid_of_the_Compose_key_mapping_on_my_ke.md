---
title: "How to get rid of the Compose key mapping on my keyboard?"
date: 2010-09-20
forum: Desktop Environments
---

### Post by Sab38Sam73 on 2010-09-20
Hello everybody,

I would like to get off the [Compose] key of my keyboard, and get back my [Control_L] key.

I want to use my keyboard as I used to. But now, I have a [Compose] key in place of my [Control] left key.

Firstly, my system is "Ubuntu Netbook Remix 10.04.1 LTS".
And here is what I tried:


1.
```
$ xev
```
  &#8594; result: the key is working


2.
  using the Gnome GUI to set up the [Compose] mapping &#8594; result: I got a new one, but nothing changed with the 1st


3.
```
$ xmodmap -e 'keycode 37 = Control_L'
```
  &#8594; result: here, "xev" shows that the mapping is now well set up; but for me, nothing changed


4.
created "~/.Xmodmap" with one line:
```
"keycode 37 = Control_L"
```
  &#8594; result: the file is loaded when I log in, but nothing changes at my fingers


5.
again with the Gnome GUI, I tried to change with other mappings (spanish, italian, etc.)
  &#8594; but still no change in the way I wanted; the [Compose] mapping gets sticked to my keyboard


6.
logged out/in; rebooted
  &#8594; result: guess what... :-(


So, I'm asking for help: 
  · If you know this situation, how did you get rid of that problem?
  · If you didn't face it up until now, what would you do in order to resolve this?


Thank you for any idea!


[added the 24th]
So, here is my solution : 1. launch **gconf-editor** 2. select **/desktop/gnome/peripherals/keyboard/kbd/options**, and disable the key.


-- 
Sabine

---

