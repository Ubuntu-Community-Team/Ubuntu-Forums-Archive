---
title: "Gnome - do NOT change focus?"
date: 2011-09-18
forum: Desktop Environments
---

### Post by zami on 2011-09-18
Is there any way I can get Gnome to NOT change focus when starting/handling programs?

For example, if I start up Firefox, Evolution, gEdit, and Synaptic all about the same time, Evolution takes two minutes, Firefox takes 8 seconds, gEdit takes .1 seconds, and Synaptic takes maybe 10 seconds and also asks for a password.  

The times don't bother me.  (Well maybe Evolution is stupid slow, but that's Evolution.)

The focus change REALLY bothers me!  I'm halfway finished typing in my notes in gEdit, when Firefox pops up and suddenly I'm typing my note into the URL bar - I delete that, finish my note, maximize Firefox again, start typing in the URL I want, but the password request from Synaptic has popped in front of it, capturing the last two characters and "enter" from the URL and entering it as a wrong password.  So I wait for that to get back to me with the "password incorrect message" (because I know that's just going to pop up on top of something else if  don't just wait), shrink it down, attempt to retype the URL entry, but now Evolution pops open and I'm filtering my inbox for "r.com".  So I shrink that down.... 

it's just a mess, and it's silly.  Is there a way to just have all this stuff open and politely wait in the panel, or a lower "level" window, instead of rudely placing itself right under my cursor?

-zami

---

### Post by zami on 2011-09-18
While entering in the one tag that made sense, I saw "focus stealing" pop up as a similar tag, so started searching with that term.

I found this tidbit... 

gconf-editor > apps > metacity > general
and changing "focus_new_windows" from "smart" to "strict"

Works great, so long as I'm launching from the terminal, which I never do.  I usually launch from the alt+F2 "run" box.

Buuuuut, at least I'm somewhat comforted to see this is an age old issue, universally loathed?  I'm also somewhat disheartened... if it's an age old issue, why is it still an issue?  
:(

I really hope I am just overlooking some option within Gnome.

I love Gnome.  I like XFCE.  I don't like KDE.  I haven't tried any other environments.  Do either XFCE or KDE handle this issue better than Gnome?  Any other environment I should try? 

-zami

---

