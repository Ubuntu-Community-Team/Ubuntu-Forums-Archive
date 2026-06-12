---
title: "How to disable mouse hiding on touch screen?"
date: 2022-09-06
forum: Desktop Environments
---

### Post by nick240 on 2022-09-06
I am using ubuntu 22.04 on my laptop which has a touch screen. The touch screen is a little buggy and sometimes ghost taps, which causes my mouse to be hidden. Is there anyway to disable the mouse hiding when using touch screen? I do not see it in gnome tweaks or ubuntu settings.

---

### Post by him610 on 2022-09-07
Yes, one can disable the trackpad if desired. I have defined an alias that resides on my laptop (which unfortunately not presently using) that call from a terminal command line. I will crankup that laptop later today and provide you with the code fragments.
Meanwhile, you can take a look at this.... [https://askubuntu.com/questions/1165445/is-there-a-way-to-toggle-touchpad-on-off-with-a-command-keyboard-shortcut]("https://askubuntu.com/questions/1165445/is-there-a-way-to-toggle-touchpad-on-off-with-a-command-keyboard-shortcut")

---

### Post by him610 on 2022-09-08
Well, it took a little longer to get back to you than I anticipated.
This is what I use to enable/disable my trackpad....
```
 
alias trkoff='synclient TouchpadOff=1'
alias trkon='synclient TouchpadOff=0'

```
I have the two aliases defined in my *.bash_aliases* file that is called by *.bashrc* when I open a terminal.

---

### Post by nick240 on 2022-09-09
> **him610 said:**
> Well, it took a little longer to get back to you than I anticipated.
This is what I use to enable/disable my trackpad....
```
 
alias trkoff='synclient TouchpadOff=1'
alias trkon='synclient TouchpadOff=0'

```
I have the two aliases defined in my *.bash_aliases* file that is called by *.bashrc* when I open a terminal.
Thanks for the reply but I mean disabling the touch screen not the track pad. My laptops screen is like a phone you can touch it. I need to disable that. When you use the touch screen it hides the mouse because it goes into touch screen mode. I want to disable the mouse from hiding or disable the touch screen

---

