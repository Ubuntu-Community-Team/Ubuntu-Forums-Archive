---
title: "I really messed this up and I need some serious help!"
date: 2008-01-08
forum: Desktop Effects &amp; Customization
---

### Post by moebob24 on 2008-01-08
I just set all my windows to complete transparency and now I can find the buttons to change it back. :(:(:(
 Is there a way to reverse this? 

Please help me all I can see is my wallpaper and the one icon on my desktop.

EDIT:
I am using Compiz-fusion if that helps.

---

### Post by Corvo78 on 2008-01-09
Okay, you could try this:

In case you aren't at your desktop yet, do so.
At your desktop press ALT-F2 (this brings up the 'run' dialog, in your case it is invisible).
Now type this:
```
metacity --replace
```
and then press your Enter key.

If all goes well Compiz is replaced with Metacity (Gnome's default window manager).
Since Metacity doesn't share Compiz's settings, things should be visible again.

Btw, even in Metacity you can use Compiz's settings manager to change the transparency to something *ehm* more useable ;)
If you changed the transparency option and feel confident to try Compiz again, hit ALT-F2 and type:
```
compiz --replace
```
and press Enter.


Goodluck!

---

### Post by Forlong on 2008-01-09
After system boot, choose the GNOME failsafe session in GDM, this will start GNOME without Compiz.
There you can run ccsm and reset things.

---

### Post by rune0077 on 2008-01-09
Holding down Alt and scrolling the mousewheel will raise/lower transparency on whatever window you happen to be over. So you could just move the cursor to the vicinity where you think the CCSM should be, hold down Alt and scroll up - this should make the window visible so you can fix the issue.

---

### Post by moebob24 on 2008-01-09
> **rune0077 said:**
> Holding down Alt and scrolling the mousewheel will raise/lower transparency on whatever window you happen to be over. So you could just move the cursor to the vicinity where you think the CCSM should be, hold down Alt and scroll up - this should make the window visible so you can fix the issue.

Thanks for the help. I actually went into the command line interface and entered
```
metacity --replace
```

and that worked, I didnt know i could change the transparency by holding alt and scrolling that is cool. plus it wont let u go 100% so u can't pull an idiot move like me.

Thanks for the responses

---

