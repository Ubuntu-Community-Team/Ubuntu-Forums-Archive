---
title: "Frozen window manager"
date: 2006-01-28
forum: Desktop Environments
---

### Post by kabanta on 2006-01-28
By right-clicking on a Flash element, my entire window manager froze. (Note: Firefox was at full screen, so it could be that there was an error-dialogue *behind* it that I could not access.) After trying a number of key-combinations, in the end I had to power-cycle the machine.

Is there some key-combination that will get me access to the prompt in such a situation (so I could at least try killing Firefox)?

---

### Post by syklitengutt on 2006-01-28
install automatix and the: enable cntr alt del key to get into 
system monitor!!

---

### Post by GTvulse on 2006-01-28
[quote=kabanta]Is there some key-combination that will get me access to the prompt in such a situation (so I could at least try killing Firefox)?[/quote]

Try getting into a console. Type CTRL-ALT-F[x] where x is a function key between 1 and 6 inclusive. Log in to your account, type "sudo killall firefox". Then type CTRL-ALT-F7 to return to your X Windows session.

[quote=syklitengutt]install automatix and the: enable cntr alt del key to get into system monitor!![/quote]

What does automatix has to do with kabanta's problem at all? Frankly, that automatix pushing all over the forums, sounds to pure shill to me; automatix imposes some very poor system security decisions behind the back of the luser (It seems to me like it was designed by the [Bastard Operator from Hell]("http://bofh.ntk.net/Bastard.html"); it takes one BOfH to recognize another on sight ;-)).

The advice to bind the system monitor to CTRL-ALT-DEL is a good idea, but won't do you any good if X Windows is frozen (been there, done that).

---

### Post by kabanta on 2006-01-29
[QUOTE=dradul]Try getting into a console. Type CTRL-ALT-F[x] where x is a function key between 1 and 6 inclusive. Log in to your account, type "sudo killall firefox". Then type CTRL-ALT-F7 to return to your X Windows session.
[/QUOTE]

This is EXACTLY what I was looking for -- thanks!

(Note: for anyone else reading this later. If "firefox-bin" isn't aliased to "firefox", the "sudo" command above won't work. One option: try instead to find the process ID with "ps -A" and then do "kill -9" on the ID number for the app that seems to have hung.)

---

