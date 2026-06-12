---
title: "speech-to-text?"
date: 2006-05-09
forum: Desktop Environments
---

### Post by dannysauer on 2006-05-09
So, Linux is all mature 'n stuff now.  And my wife hurt her right arm (well, the nurse did - next time the life insurance people send an 83 year old shaky-handed nurse over to do the physical, we may elect to have blood drawn elsewhere) so she can't type real well.  And I thought "hey, maybe there's good speech recognition stuff out there!"

Hmph. ViaVoice seems to have been gone for years, Sphinx looks promising but doesn't seem to actually do anything aside from providing an engine you can write a program around, etc.  Festival's got lots of neatness - if I want my computer to read to me.  No, I want to dictate text to a word processor.  XVoice appears to be an acceptable front end, but since viavoice isn't available anymore and the sphinx conversion project has stalled, well, it's not much help without a backend. [http://xvoice.sourceforge.net/xvoice-sphinx/](http://xvoice.sourceforge.net/xvoice-sphinx/)

I could do this with ViaVoice nearly a decade ago.  What can I do that with now?  Surely by now *someone* has developed something to keep my wife from having to use the mouse and keyboard so much...

Does anyone have any experience / suggestions?

---

### Post by louis_nichols on 2006-05-10
This is a really interesting issue. I'm sorry if this might not be any real help, but did you try actually using the old versions of the packages you wrote were once working? They might still compile (in an old dusted corner of the web you might still find this IBM sdk they say is missing)... Or, in xvoice's case, try to use alien on the rpm for redhat.

---

### Post by dannysauer on 2006-05-10
I don't have any old versions anymore, and since old ViaVoice wasn't free (there was some minimal fee to license it), it's nlikely to be available for download in a lot of reptable places. :)

Xvoice would probably install, and there are packages for sphynx in the Ubuntu repository.  But since XVoice says it doesn't really work well at all, and says that it works best on older Linuxes like RedHat 6 but doesn't really work well even then with sphynx, I'm not sure it'd be worth the effort. :)

---

### Post by dannysauer on 2006-05-10
I'm gonna try [http://perlbox.org/pbtk/](http://perlbox.org/pbtk/) tonight, hopefully (though it doesn't take dictation, either)...

---

### Post by louis_nichols on 2006-05-10
well... good luck, then!

Please post your results! One never knows when they might need such a thing.

---

### Post by killerrobot on 2006-05-17
Have you found anything that works?   I'm also injured and trying to get some work done...

---

### Post by Edward The Bonobo on 2006-05-17
I know there's an Accessible Ubuntu group...I'm wondering...would there maybe be some mileage in putting together an Accessibility HowTo.  I't quite like to do one, if someone can point at some relevant resources.  It would have to cover stuff like:

[LIST]
[*]speech-to-text
[*]text-to-speech (including screenreaders etc)
[*]Increasing screen visibility (large text, palettes, etc)
[*]Typing aids - sticky keys, predictive text, etc
[*]Alternate output devices (braille, domestic device controllers)
[*]Alternate input devices - scrolling alpha, non-standard keyboards, etc.
[*]Other stuff - suggestions welcomed.
[/LIST]

---

### Post by dannysauer on 2006-05-17
I pulled the program down and looked at its capabilities, and decided that it wasn't going to do what I wanted.  For some automation, it may well work, but apparently Sphinx isn't very reliable, and as I already knew, it won't take dication - so it seemed a waste of time.  Sorry I don't have useful results to post back...

---

### Post by Henrik on 2006-05-19
Edward,

Some work has been done already on accessibility documentation, but more help is always needed. I've written a getting started guide here: [https://wiki.ubuntu.com/Accessibility/doc/StartGuide](https://wiki.ubuntu.com/Accessibility/doc/StartGuide) (and that one should not grow much more), but there are several documents here [https://wiki.ubuntu.com/Accessibility/doc](https://wiki.ubuntu.com/Accessibility/doc) that could do with updating or expanding. 

Thanks! :)

---

