---
title: "Grainy screen on 10.04 boot"
date: 2010-04-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by r.masters on 2010-04-30
Launchpad doesn't seem to be working atm, so I'll leave this here till I can try and post it again.

Grainy screen on boot/resume

Package error with: xorg (poss. xsplash).

When I boot Lucid (10.04 LTS) the following things happen:

[list=1]
[*] The ubuntu splash briefly shows,
[*] Then a grainy screen is displayed. This is rather similar to the screen's you'd get on an analogue TV when it isn't tuned to a station. On a boot from shutdown this occurs for a second.
[*] Then the login screen shows.
[/list]

Obviously the expected action is the grainy screen not occurring.

If I am resuming from hibernation, the grainy screen stays for longer and does not seem to recover to the login screen. You can move the mouse pointer (a slightly lighter patch of grainy screen moves around) although it disappears in the middle of the screen, presumably for the login box.

This has only occurred since 10.04. I haven't been able to get past the grainy screen if I resume from hibernation (although I think I managed to log in blindly once).

Anyone else experiencing this? I'm on a Dell Studio 1555.

---

### Post by peterbengtsson on 2010-05-10
I'm experiencing the exact same problem! like you say, restarting gdm (logging out and in again) solves it. 

Have you figured out what might cause it? I really hope someone can step up and figure this one out.

---

### Post by peterbengtsson on 2010-05-10
Looks like we're not the only ones suffering from this:
[http://swiss.ubuntuforums.org/showthread.php?t=1306649](http://swiss.ubuntuforums.org/showthread.php?t=1306649)

---

