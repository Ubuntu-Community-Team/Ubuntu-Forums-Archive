---
title: "change the close session default"
date: 2005-03-29
forum: Desktop Environments
---

### Post by ploum on 2005-03-29
Hello,

Is it a way to change the default behaviour of "close session" in the system menu ?

I think that most of desktop users often shutdown their computer but never change session (and don't know about it).


My mother don't want to use the System (one click) > Close session (one click) > change the radio button to shutdown (one click) , Ok (one click) = 4 clicks !!!

I've written a small zenity script that ask for confirmation before calling sudo halt (clicking on the icon (one click), Ok (one click) = two clicks) and my mother always use that, but it's a bit hacky...


Myself, on my computer, I often close the session when I want to shutdown the computer and it's very annoying !

---

### Post by TravisNewman on 2005-03-30
what is it that you want it to do exactly? Just auto restart, auto reboot, or what?

---

### Post by ploum on 2005-03-30
[QUOTE=panickedthumb]what is it that you want it to do exactly? Just auto restart, auto reboot, or what?[/QUOTE]
 I just want to enable the "shut down" radio button by default...

---

### Post by Knome_fan on 2005-03-31
Sorry for bumping this thread, but I'm having the same problems the original poster had and would also be very interested in an answer.

Also, I'd like to know what exactly gnome is executing when you call it to logout/shutdown/reboot, as this would making an easy to use shutdown button myself possible.

---

### Post by IdoMcFly on 2005-03-31
I'd like to fix the default active button too! It would be real nice!

---

### Post by IdoMcFly on 2005-05-11
So it is not possible ?

---

### Post by Alexander Kirillov on 2005-05-11
[QUOTE=ploum]Hello,

Is it a way to change the default behaviour of "close session" in the system menu ?

I think that most of desktop users often shutdown their computer but never change session (and don't know about it).


My mother don't want to use the System (one click) > Close session (one click) > change the radio button to shutdown (one click) , Ok (one click) = 4 clicks !!!

I've written a small zenity script that ask for confirmation before calling sudo halt (clicking on the icon (one click), Ok (one click) = two clicks) and my mother always use that, but it's a bit hacky...


Myself, on my computer, I often close the session when I want to shutdown the computer and it's very annoying ![/QUOTE]
 On most modern (less than 3 years) computers, you can just press the power button, and it will cleanly shutdown the computer (ACPI will catch the event, call shutdown script, etc..)

---

