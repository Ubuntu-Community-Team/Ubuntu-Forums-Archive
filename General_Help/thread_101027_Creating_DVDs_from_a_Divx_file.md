---
title: "Creating DVDs from a Divx file"
date: 2005-12-08
forum: General Help
---

### Post by kairu0 on 2005-12-08
I am a n00b when it comes to Linux DVD authoring. I would like to know whichever program you think is best for creating DVDs from a Divx avi file exclusively through a GUI.

---

### Post by BLTicklemonster on 2005-12-09
I think it's called tmpgenc, and you'd have to run it in wine. If it will work in wine. I had "something" and made a pretty darned good dvd out of it just the other day, but tmpgenc isn't free. I hope someone comes along with a linux alternative. 

Good question.

---

### Post by BLTicklemonster on 2005-12-09
[http://www.google.com/linux?q=convert+avi+to+dvd&btnG=Search&hl=en&lr=](http://www.google.com/linux?q=convert+avi+to+dvd&btnG=Search&hl=en&lr=)

Apparently there's some, but looking about quickly, I didn't see any free ones.

---

### Post by BLTicklemonster on 2005-12-09
[http://www.bunkus.org/dvdripping4linux/single/](http://www.bunkus.org/dvdripping4linux/single/)

Pretty complicated, waaaay above my head, but looks like it deals with avi to dvd. 

I'm assuming this will work with divx. I'm a noob in this area, sorry.

And this one is about capturing, but towards the end it takes avi and makes it a dvd: [http://linuxgazette.net/issue83/stoddard.html](http://linuxgazette.net/issue83/stoddard.html) I hope these help.

---

### Post by kairu0 on 2005-12-09
Thanks for your replies.

I'll take a look at those links.

---

### Post by BLTicklemonster on 2005-12-09
[QUOTE=kairu0]Thanks for your replies.


Are you telling me that you don't know of a free Linux application to do this? I was hoping there would be a Gnome or KDE dvd authoring wizard or something.

[/QUOTE]

Those last ones deal with what you need to roll your own. :) :rolleyes:

---

### Post by timczer on 2005-12-09
I was able to do this with a combination of two softwares.  Avidemux to take the avi and put it into an mpeg format that can be read by a dvd player and then Varsha to turn that file into a dvd iso.  I am pretty sure that you will need to download Varsha from the link, I am not 100% sure if Avidemux was in the repositories or if I found the .deb.  The tutorial I used has links to the needed programs and I don't think any were difficult to get working.  Here is the link to the tutorial I used for this: [http://www.videohelp.com/forum/viewtopic.php?t=242455]("http://www.videohelp.com/forum/viewtopic.php?t=242455")

---

### Post by kairu0 on 2005-12-10
Thanks to both of you. I didn't want to use any commercial software and I couldn't understand that tutorial very well, so I tried something else.

Using this tovid howto ([http://tovid.sourceforge.net/howto.html](http://tovid.sourceforge.net/howto.html)) I was able to make a dvd disc very easily. It also plays on my living room dvd player.

---

### Post by timczer on 2005-12-10
Cool, I am glad you found something that worked for you.  I will have to check out Tovid to see if it is easier than the others.  For anyone else wanting to look at avidemux or varsha, they are not commercial apps.  Both are available for download through the link provided above and are free software.  (not sure about open-source or not).

---

### Post by kairu0 on 2005-12-10
Yeah, I know that they aren't commercial apps. I just couldn't figure out how to use them with that tutorial.

---

### Post by Drain on 2005-12-10
[QUOTE=timczer]Cool, I am glad you found something that worked for you.  I will have to check out Tovid to see if it is easier than the others.  For anyone else wanting to look at avidemux or varsha, they are not commercial apps.  Both are available for download through the link provided above and are free software.  (not sure about open-source or not).[/QUOTE]

I'll second using [Tovid]("http://tovid.sourceforge.net/").  It's pretty easy to pick a couple of Xvid or Divx files, and have them be converted to a dvd format - it even makes a simply-titled menu.  The GUI has an easy to follow layout, and their webpage has a walkthrough.

---

### Post by jtpratt on 2006-03-22
I tried Varsha too, and it kept giving me errors.  There is a new one called DeVeDe, but I've not been able to get it to work at all.  Everytime I fire it up and go to open a video to convert it locks.  

Tovid on the command line has been good to me, the GUI won't work for me at all.  I documented all the tools I found and use in Ubuntu in my [video help guide]("http://smorgasbord.net/convert_video_linux").

---

