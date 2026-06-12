---
title: "Disable right mouse button"
date: 2006-09-24
forum: Desktop Environments
---

### Post by totvos on 2006-09-24
Hello everyone,

I have recently installed Ubuntu onto an old computer I had lying around for my 2.5 yr old to start playing around with. My goal is to get a completely open source system, suitable for kids. Generally, it is working EXCELLENTLY. However I have noticed that when he is poking around with his Flash-based games, he will invariably hit the right mouse from time to time, causing the annoying Flash context menu to pop up.

What I would like to do is lock down the right-mouse behaviour on his account so that it behaves just like the left mouse.

It has been ages since I have used Unix, and really don't know a whole lot about Linux and GNOME, but I am a long-time programmer guy. I have been Googling this problem for a while now and am surprised there is no immediately obvious solution, although I don't doubt that with all the conf files lying around a solution is possible.

Any words of wisdom from anyone would be greatly appreciated.

Thanks in advance,

-- tomo

---

### Post by totvos on 2006-09-25
For those with the same problem, I have come up with a solution. It may not be the *right* solution, but it works. I would still like to appeal to Ubuntu experts to help point me down the true path.

As for my solution, I first used info from various HowTos regarding mouse mappings, by modifying the xorg.conf file and adding a ButtonMapping Option to the mouse InputDevice:

[INDENT]Option "ButtonMapping" "1 1 1"[/INDENT]

This works, of course, because it maps all mouse buttons to button 1 when the X server starts up. The real problem is that it is a system-wide setting, and I could not find a way to have user-specific xorg.conf files.

I also tried working with xmodmap to change the button mappings there, but was confronted with errors either telling me that I need to specify values for all 9 mouse buttons (!!!), or that a value was out of range. It seems that regardless of how many mouse buttons you have, you need to specify 9 values, AND the values all have to be unique. So doing the following does not work:

[INDENT]xmodmap -e "pointer = 1 1 1 1 1 1 1 1 1"[/INDENT]

But, the following DOES WORK:

[INDENT]xmodmap -e "pointer = 1 9 8 7 6 5 4 3 2"[/INDENT]

Since I don't have 9 buttons on my mouse, this effectively disables buttons 2 and 3, my desired result. The bonus of using xmodmap is that I can now put it into a user-specific .gnomerc file in the $HOME directory of the users I want to have this crippled behaviour.

I would be happy to hear of other solutions.

-- tomo

---

### Post by Merlum on 2008-01-27
Hello,
I did the trick by mapping mouse buttons #2 and #3 to #8 and #9 like this:
xmodmap -e "pointer = 1 8 9 4 5 6 7 2 3"

You need to specify all 9 buttons if you want to map the 3rd button to 9th position.
xmodmap -pp prints the current configuration.

Cheers,
Thierry

---

