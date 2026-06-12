---
title: "Zsnes, Suddenly Way Too Fast, Sometimes Without Sound"
date: 2006-03-11
forum: Gaming &amp; Leisure
---

### Post by dpaint4 on 2006-03-11
When I first installed Zsnes, my favorite SNES/Super Famicom emulator, it was effortless and perfect. The longer I use it the stranger it behaves.

It is now running way way way too fast, and there seems to be no way to limit the speed through the command line or the gui.  This speed problem effects both frame rate and sound.

Additionally, it no longer plays any sound at all unless opened from within the Terminal. I used to be able to use a shortcut on my desktop, or within the Gnome Applications/Games menu. Now, when I do that the program starts without audio.

Starting it with a simple /usr/bin/zsnes effectively starts it from the Terminal with sound intact, but no matter how I start it the damn thing is running like eight times too fast.

I'd love to hear other people's similar experiences and the fixes that worked for them. Anyone?

Thanks for the input. You guys seem to know just about everything.

---

### Post by BoyOfDestiny on 2006-03-12
[QUOTE=dpaint4]When I first installed Zsnes, my favorite SNES/Super Famicom emulator, it was effortless and perfect. The longer I use it the stranger it behaves.

It is now running way way way too fast, and there seems to be no way to limit the speed through the command line or the gui.  This speed problem effects both frame rate and sound.

Additionally, it no longer plays any sound at all unless opened from within the Terminal. I used to be able to use a shortcut on my desktop, or within the Gnome Applications/Games menu. Now, when I do that the program starts without audio.

Starting it with a simple /usr/bin/zsnes effectively starts it from the Terminal with sound intact, but no matter how I start it the damn thing is running like eight times too fast.

I'd love to hear other people's similar experiences and the fixes that worked for them. Anyone?

Thanks for the input. You guys seem to know just about everything.[/QUOTE]

Not sure about the sound issue... But for speed...
Did you go to Config -> Speed? Make sure auto frame rate is checked...

[[IMG]http://img156.imageshack.us/img156/6681/screenshotzsnes10na.th.png[/IMG]](http://img156.imageshack.us/my.php?image=screenshotzsnes10na.png)
(Hope that menu option is in your version... I've been running the CVS (basically what will become the next release)... 
Hope this helps you!

---

### Post by dpaint4 on 2006-03-12
Thanks. Yep. I've got auto-frame rate checked. Experimented with it both ways just in case there was something I was missing.

I've been using Snes9X with a front-end since this issue resulted, and it seems to have all the compatibility I had with ZSNES, so I think I'll just uninstall ZSNES and accept the loss (not so honorable, but currently it's the *only* thing not working on my otherwise nicely configured laptop, so I'm willing to just sacrifice it since there's a good alternative).

Still if anyone has had a similar issue and resolved it (or not resolved it) I'd love to  hear about it.

EDIT: WOW! I just noticed your screenshot. NO. I don't have that menu at all and I'm totally jealous. That'd completely fix my issue if I could access that. I guess I'll hang onto the emulator and wait for that version to be released officially. Thanks for light at the end of the tunnel.

---

### Post by BoyOfDestiny on 2006-03-13
Well good you have an alternative, I've just gotten so used to zsnes... I had used snes9x back before it was called that (snes96 and 97 :) )... Anyway, if you are feeling adventurous, compiling the cvs can be a good learning experience. Or when you move to dapper, and I get my page together, debs will be there. I want more emulation enthusiasts to move to Linux ;)

---

### Post by dpaint4 on 2006-03-13
I'm totally adventurous. I will look into it. I just installed Wine today and that in itself was a fantastic adventure.

I'm not ditching ZSNES just yet. I want to at least try the version you're using when it becomes the standard version.

---

### Post by arcanistherogue on 2006-03-13
FZero would be amazing at that speed.

---

### Post by pagefault on 2006-03-16
Delete your ~/.zsnes folder and try again this may fix your problem. Also are you running on laptop?

---

