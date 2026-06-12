---
title: "Tomboy Keybindings not working"
date: 2005-04-14
forum: Desktop Environments
---

### Post by shu on 2005-04-14
Hi!

I have a problem with tomboy. It's global keybindings ALT+F11/ALT+F12 don't work for me. Any ideas what might be wrong?

---

### Post by shu on 2005-04-19
Am I on my own with this problem?  :???:

---

### Post by Bob D. on 2005-04-19
Just tried it here and the hotkeys work.

Does this happen with both ALT keys? Do you have another keyboard to try? Can you think of any software you installed that might interfere? I don't know if any of this matters, I'm just to throw out some ideas for you.

Bob

---

### Post by shu on 2005-04-19
Well, I just installed hoary and added tomboy to it. No special software. And tomboy runs ok on the same computer on different distro. I have no clue, what might be wrong. :/

---

### Post by GeneticFreek on 2005-04-19
My Tomboy keybindings don't work either. I have a MS natural keyboard where the function keys try to turn themselves into other things (copy, paste, etc), which is really annoying, but after I turn them back to function keys I still get nothing.

---

### Post by shu on 2005-04-20
Well, I can't believe it. But it's true. If I turn numlock off, shortcuts work, if I turn it on, they don't. How can this be??!

---

### Post by Bob D. on 2005-04-20
[QUOTE=shu]Well, I can't believe it. But it's true. If I turn numlock off, shortcuts work, if I turn it on, they don't. How can this be??![/QUOTE]I don't know but I just tried it here and, sure enough, with the numlock on my Tomboy shortcuts stop working. No idea how or why, but I'd suggest filing a bug against Tomboy.

Since they don't have a bug tracker in place, I'd either email the  author [email="alex@beatniksoftware.com"]here[/email] or post to the mailing list [here]("http://beatniksoftware.com/mailman/listinfo/tomboy-list_beatniksoftware.com"). I'm dropping an email to the author, so if you guys will as well that should help get this on the list to be fixed.

Bob

---

### Post by shu on 2005-04-20
I'm not really sure if it's tomboy's fault. I have it running in slackware with numlock on without any problems. 

I also noticed that turning cups lock also disables tomboy bindings. However you can switch cupslock behaviour [in keyb. pref.] from 'default' to any other setting and then things are back to normal. I didn't found anything like that for numlock though.

---

### Post by wjp.reg on 2005-11-18
Here it is half a year later and the keyboard bindings are still a problem?

toggling the NumLock "off" does work, (using MS Natural kybd), but do I really want to do that all the time?

Anyone else still having this problem?

I understand version 0.3.3 is out but not yet available in port ;) 

Someone more experienced?

Thanks!

---

### Post by blink on 2007-02-22
I suspect it's something about your keyboard definition that is the problem. Tomboy is probably the program where you see the problem, not the cause of the problem.

I have a Dell Inpsiron Laptop and have no problems with the keybindings (with or without caps lock and/or num lock).

You may wish to try the program "xev". ("sudo apt-get install xev" if necessary) It will pop up a window. Move focus into the window and it will flood your terminal with all the x events going on. press alt-f11 and see what x events are reported. maybe your keyboard definition is redefining the f11 key when you have numlock on?

---

