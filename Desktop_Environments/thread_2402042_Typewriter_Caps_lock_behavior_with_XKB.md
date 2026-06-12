---
title: "Typewriter Caps lock behavior with XKB?"
date: 2018-09-25
forum: Desktop Environments
---

### Post by MiSt77 on 2018-09-25
[COLOR=#222222][FONT=Verdana]I have to admit that I have already asked this question before (in [/FONT][/COLOR][2010]("https://ubuntuforums.org/showthread.php?t=1586506")[COLOR=#222222][FONT=Verdana]). Regrettably, however, I didn't receive any responses back then.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Quite some time has passed since, but despite having searched for a solution over and over again, I still haven't found a way to coerce XKB's Caps lock handling to behave like a manual typewriter. I.e. to turn off Caps lock, you have to press Shift. That is, no matter how often I press Caps lock, it should stay in uppercase mode, only to revert to lowercase after I press Shift:[/FONT][/COLOR]

[FONT=courier new][COLOR=#222222]aaaa <Caps> AAAA <Caps> AAAA <Shift> aaaa[/COLOR][/FONT]

[COLOR=#222222][FONT=Verdana]I guess with X11 being phased out, and many Linux distributions now preparing the switch to Wayland, the input handling stack must've undergone several changes in the last 10 years. Is there anyone who knows if Typewriter-style Caps lock behavior has finally become available under XKB? (I have, of course, already enabled XKB's [/FONT][/COLOR][FONT=courier new][COLOR=#222222]shift:breaks_caps[/COLOR][/FONT][COLOR=#222222][FONT=Verdana] option, but that is only part of the equation.)[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Thank you :-)[/FONT][/COLOR]

---

### Post by him610 on 2018-09-25
MiSt77,

I don't know if you are aware of this site....[https://medium.com/@damko/a-simple-humble-but-comprehensive-guide-to-xkb-for-linux-6f1ad5e13450]("https://medium.com/@damko/a-simple-humble-but-comprehensive-guide-to-xkb-for-linux-6f1ad5e13450")

The writer, Damiano Venturin, seems to know a good bit about *xkb*. You might want to contact him.

---

### Post by MiSt77 on 2018-09-26
him610,

Yes, I've stumbled over this (actually readable) introduction to XKB several times over the years. And I agree: Damiano Venturin comes off as someone who is quite knowledgeable about XKB, its configuration, and how it accomplishes everything it does.

That being said, I never thought of contacting him directly, but this actually does sound like a good idea.

Thank you for this suggestion!

---

### Post by MiSt77 on 2018-10-19
Following user him610's advice, I contacted the author of "A simple, humble but comprehensive guide to XKB for linux". However, while Damiano Venturin generously thought about my problem, and provided me with several suggestions on how I could tackle this issue, none of the multitude of XKB's knobs seemed to provide a real solution.

In the end, I've found that the only way to force „Typewriter Caps lock“ is to modify the Systems event handling logic in a file called „evdev.c“, which ships in the following packages:

[LIST]
[*]X11 based distributions: xserver-xorg-input-evdev package
[*]Wayland based distributions: libinput10 package
[/LIST]
[COLOR=#242729][FONT=Arial]For all technology savvy users interested in this solution: I've just recently posted a step-by-step guide on [/FONT][/COLOR]*GitHub*[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]
[Typewriter Caps lock with evdev and libinput]("https://github.com/Cordic77/xkb-typewriter-caps")

However, for the time being, I intend to keep this thread open – I'm still hoping that someone may be able to suggest a less intrusive course of action …

---

