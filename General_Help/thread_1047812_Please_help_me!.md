---
title: "Please help me!"
date: 2009-01-22
forum: General Help
---

### Post by Meohme3 on 2009-01-22
My Mozilla Firefox keeps crashing whenever I view stuff like Youtube videos, Runescape Website, Myspace account page, etc. And I was looking at the results of "top" and it said my cpu memory overloaded, I don't know if this means I have to delete programs. Please help me.

---

### Post by grndslm on 2009-01-22
Upgrade to flash 10 for starters

---

### Post by Meohme3 on 2009-01-22
flash 10? do you mean adobe or what???

---

### Post by sofasurfer on 2009-01-22
Adobe 10 is adobe flash player.

---

### Post by Meohme3 on 2009-01-22
I have adobe flash player.

---

### Post by sofasurfer on 2009-01-22
I recommend following "Comprehensive Multimedia & Video Howto". This solved all my video problems.

---

### Post by grndslm on 2009-01-22
> **Meohme3 said:**
> flash 10? do you mean adobe or what???Never heard of the Goog?

And what version of flash do you have?

---

### Post by Meohme3 on 2009-01-22
I have 10, I don't think my flash player is my problem though.

---

### Post by grndslm on 2009-01-22
I think it is.  Uninstall flash and prove me wrong.

All those sites you listed are flash-based.  At least I'm guessing for runescape, but I don't see how it couldn't use flash.

---

### Post by Chops II on 2009-01-22
runescape is Java, actually

---

### Post by Meohme3 on 2009-01-23
Yes it is, and I need to know how to figure this out, it's not a debate room.

---

### Post by mb_webguy on 2009-01-23
> **Meohme3 said:**
> My Mozilla Firefox keeps crashing whenever I view stuff like Youtube videos, Runescape Website, Myspace account page, etc. And I was looking at the results of "top" and it said my cpu memory overloaded, I don't know if this means I have to delete programs. Please help me.

When you run "top", type ">" to sort the list by processor usage.  What processes are hogging your CPU?  Now type ">" again to sort by memory usage.  Is some process using an inordinately high percentage of your memory?

I agree that the likely culprit is Flash.  What version of Ubuntu are you using?  This was a common problem in Hardy, but seems to have been fixed in Intrepid.  One option (if you are using Hardy) is to install the [Intrepid version of Flash]("http://packages.ubuntu.com/intrepid/flashplugin-nonfree") (but make sure you first uninstall the current version of flashplugin-nonfree and (if necessary) libflashsupport.

---

### Post by avtolle on 2009-01-23
Another thing to check: is Gnash installed as well? IIRC, the default Firefox on a new install comes with Gnash installed. If it is, it could well be conflicting with the Adobe Flash. In the Firefox browser bar, type "about:plugins" (without the quotes) to see what comes up. If Gnash is present, you will need to uninstall it, using your method of choice. Another thought: on Java sites, generally the open-source Java is installed in Ubuntu by default (again, from memory). While it (the open source) does a good job for many things, it doesn't do well with Runescape. You will need to install the sun java, and select it as your preferred java client. Good luck.

---

### Post by zami on 2009-01-23
I'm sorry you've gotten some argumentative responses.

As one helpful poster did suggest, I'd follow the 
"Comprehenisve Multimedia & Video Howto", which is here
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Even if you think you've already got some things running just fine, I'd follow the entire thread.  If you look in Synaptic, you'll see there are quite a few Flash players (couple versions of Adobe's Flash, the gnash player, the one with "mozilla" in the title, etc), and I've found when you have more than what you want installed it gets confusing - even more so when you start installing all the dependencies and end up with gstreamer and xine and who knows what else - next thing you know you've got sound on youtube but the Totem movie player doesn't work - it can be maddening!  That thread is a really nice walkthrough so you don't have to play the mix'n'match game in Synaptic.

Good luck, hope you get something figured out.

-zami

---

