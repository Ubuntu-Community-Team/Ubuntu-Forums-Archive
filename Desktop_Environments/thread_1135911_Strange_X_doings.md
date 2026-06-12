---
title: "Strange X doings"
date: 2009-04-24
forum: Desktop Environments
---

### Post by rayk_sland on 2009-04-24
Have an IBM Netvista, just upgraded to Jaunty, with a black Screen in X problem

Have read and tried all the Black Screen tips, tried several different cards, same problem. 

Diagnostic method: 
X -configure
X -config /root/xorg.conf.new

For the past few years the above has always gotten me workable xorg.conf files to tweak.

This one, the monitor goes through some mode switching and remains black

I can CTRL-ALT-F2 to log in and view logs, and kill the X server. No apparent errors. Everything looks pretty good.

Strange symptom discovered by chance.
If I press the power button (momentary soft-power-down-wise,) I will for a few seconds get an X cursor on the screen and then Jaunty shuts down the machine.

It's almost as if there's some program blocking X but it dies early enough for X to start after shutdown is initiated. tried killing everything that might be "it" in the 'ps' list. No effect.

Any suggestions welcome...

---

