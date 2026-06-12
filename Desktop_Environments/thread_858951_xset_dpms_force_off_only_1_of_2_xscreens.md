---
title: "xset dpms force off only 1 of 2 xscreens?"
date: 2008-07-14
forum: Desktop Environments
---

### Post by Neovos on 2008-07-14
So here's my question:

I have my xorg.conf setup so that there is always a second separate x screen setup and waiting in case I happen to plug in a second LCD, tv, monitor, whatever. Essentially, I set it up through the nvidia-settings for a separate x screen for the 2nd lcd and X11 just disables the second if it's not detected. Awesome. Plug and play x screen and no more resolution worries when giving presentations.

So now what I want to do is be able to turn off one screen or the other based on what I am viewing. Sometimes I'll be watching a movie on one and checking my mail on the other, but as soon as I finish the mail and just want to finish the movie, I want to turn that particular lcd off and leave the other x screen on. Is this possible?

I have this as a hotkey for turning off my lcd when I don't want to close the lid:
```
brian@Apollo:~$ sleep 1 && xset dpms force off
```
But it turns off both screens. I tried fiddling around with the -display option, but I think that refers to a monitor on a different machine? 
```
usage:  xset [-display host:dpy] option ...
```
I tried a couple different things:

```
brian@Apollo:~$ xset -display :0 dpms force off
```
which worked but turned off both screens as before
```
brian@Apollo:~$ xset -display :1 dpms force off
xset:  unable to open display ":1"
```
didn't work
```
brian@Apollo:~$ xset -display Screen0:0 dpms force off
```
which hung indefinitely. Am I looking in the right spot for this? or is there a different way to talk to the other X server?

---

### Post by Neovos on 2008-07-22
OK so some progress. When both xscreens are running, I open a terminal in one and get this:
```
brian@Apollo:~$ echo $DISPLAY
:0.0

```

and in the other xscreen terminal:
```
brian@Apollo:~$ echo $DISPLAY
:0.1

```

so this is good. But regardless of putting in this:
```
brian@Apollo:~$ xset -display :0.0 dpms force off

```
or this
```
brian@Apollo:~$ xset -display :0.1 dpms force off

```

It turns them both off. My guess is that the -display thing is ok but it's overridden by the "dpms" because that then governs all screens that are "dpms" enabled. But I can't figure out how to turn dpms off in one screen and leave it on the other. Any ideas?

---

### Post by katjapurrs on 2008-10-27
:popcorn:
Hi,
Did you ever find a solution? I'm trying to do the same thing. I have a CRT screen that I use for computer-y stuff and a TV for HTPC-type stuff.

Before I had the CRT on here I just used *xset dpms force off* but now of course that turns off both screens.:mad:

---

### Post by Neovos on 2008-10-31
> **katjapurrs said:**
> :popcorn:
Hi,
Did you ever find a solution?

unfortunately not. I actually added a laptop to my arsenal and got rid of my second lcd. So I'm able now to use the laptop for computer stuff while watching stufd on the desktop (and naturally being able to turn one or the other off). For the laptop tho, when I have a dual x screen going, I can force the laptop LCD off by closing the lid (which then turns both screens off), but then shaking a mouse or touching the touchpad. The laptop screen stays off because of hardware and the second screen going out to my tv or whatnot turns back on. So maybe the "close lid" event can be simulated and sent to a particular screen? Other than that I'm still stumped.

---

