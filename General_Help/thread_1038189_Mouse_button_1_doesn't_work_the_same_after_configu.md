---
title: "Mouse button 1 doesn't work the same after configuring compiz"
date: 2009-01-12
forum: General Help
---

### Post by Prium on 2009-01-12
Hi,
I have recently installed Ubuntu 8.04 on my laptop.Yesterday I was playing around with bindings for Expo and decided to use Ctrl-button 1 (left mouse button)as I couldn't think of any other reason I'd be using this combination. It worked perfectly fine for Expo. Now however, just pressing button 1  no longer functions as the usual mouse click. Instead a little hand appears allowing me to drag windows around. 

I just cannot see any way to reverse this. I have set the bindings back to their defaults in compiz expo. But apparently I need to change the mouse bindings back to their defaults somewhere else (which isn't avaialble in Preferences -> Mouse). 

Help would be most appreciated.

---

### Post by Loosewheel on 2009-01-12
> **Prium said:**
> Hi,
I have recently installed Ubuntu 8.04 on my laptop.Yesterday I was playing around with bindings for Expo and decided to use Ctrl-button 1 (left mouse button)as I couldn't think of any other reason I'd be using this combination. It worked perfectly fine for Expo. Now however, just pressing button 1  no longer functions as the usual mouse click. Instead a little hand appears allowing me to drag windows around. 

I just cannot see any way to reverse this. I have set the bindings back to their defaults in compiz expo. But apparently I need to change the mouse bindings back to their defaults somewhere else (which isn't avaialble in Preferences -> Mouse).
Help would be most appreciated.

Hi Prium,
From a console, type:
'xmodmap -e "pointer = default"'
With out the single quotes. And 'man xmodmap' will tell you all about that command.

---

### Post by Prium on 2009-01-12
> **Loosewheel said:**
> Hi Prium,
From a console, type:
'xmodmap -e "pointer = default"'
With out the single quotes. And 'man xmodmap' will tell you all about that command.

Thanks for your reply LooseWheel. 
I tried the command xmodmap -e "pointer = default"
It didn't say anything happened in the prompt. 
I rebooted - mouse button behavior is unfortunately unchanged. 

I also tried xmodmap -e "pointer = 1 2 3"
But this didn't change anything either. 

Should I reset the keyboard too?

---

### Post by Loosewheel on 2009-01-12
Sorry Prium, I don't know. But, 'xmodmap -e "pointer = default" -verbose' brought up some code. And 'xmodmap -pp' will output button info. Also 'xev' (put the pointer in the box app) will tell you which button is pressed, (button press event, bottom line, second txt.

What about 'System>Preferences>Avanced Desktop Effects Settings' ?
Maybe uncheck 'Expo' ?

---

### Post by shecky on 2009-01-12
It sounds like your movement key is toggled to be permanently on now. If you hold down your modifier key (alt, windows key, ctrl, whatever it's set to) you should be able to left click. Go into your window preferences and under "Movement Key" you might see all three selected. Try selecting just one. If that doesn't work, lose all patience and delete your gnome preferences folder.

---

### Post by Prium on 2009-01-12
Brilliant! 
I unchecked all but one movement key and that seems to have fixed it. 
:popcorn:
Thanks for your help guys

---

### Post by MrDelish on 2009-06-13
> **shecky said:**
> It sounds like your movement key is toggled to be permanently on now. If you hold down your modifier key (alt, windows key, ctrl, whatever it's set to) you should be able to left click. Go into your window preferences and under "Movement Key" you might see all three selected. Try selecting just one.

Worked for me, too. Odd, considering those are radio buttons and not checkboxes (in 8.10, anyway). How they all get selected at once seems pretty mysterious.

---

