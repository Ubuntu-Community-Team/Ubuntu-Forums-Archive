---
title: "MainActor"
date: 2005-10-28
forum: Desktop Environments
---

### Post by ColinG on 2005-10-28
Seeing that the video edition software Main Actor is now available as a deb package, I thought I'd give it a try on Kubuntu. Not overly successful though as
1) The picture playback on the timeline was very jerky
2) There was no sound during timeline playback.
3) When typing "mactor" in the terminal (either as user or sudo) the prog would not run (it was not automatically placed in the start menus at installation). Clicking on the application in the opt folder where it installed brought it to life.

All a little odd really. Has any body else managed to get this piece of software working on Kubuntu?

Thanks

---

### Post by suoko on 2005-10-28
1) I don't have that problem, check the forum, you'll get a quick answer
2) To get the sound working on breezy you have to use alien to convert the suse 9.3 rpm package. That's the version you have to install.
3) It's installed in /opt as many other programs. If you want to open from terminal easily just so a 'sudo ln -s /opt/MainActor_V5/mactor /usr/local/bin/'


[QUOTE=ColinG]Seeing that the video edition software Main Actor is now available as a deb package, I thought I'd give it a try on Kubuntu. Not overly successful though as
1) The picture playback on the timeline was very jerky
2) There was no sound during timeline playback.
3) When typing "mactor" in the terminal (either as user or sudo) the prog would not run (it was not automatically placed in the start menus at installation). Clicking on the application in the opt folder where it installed brought it to life.

All a little odd really. Has any body else managed to get this piece of software working on Kubuntu?

Thanks[/QUOTE]

---

### Post by ColinG on 2005-10-28
Thanks for that.

So the deb on mainactors site is no good for Kubuntu but the SuSe RPM is after using Alien. Maybe that is my problem I never used the rpm.

I'll try it tonight and once again many thanks for your help.

Colin

---

### Post by merandre on 2005-11-11
[QUOTE=suoko]1) I don't have that problem, check the forum, you'll get a quick answer
2) To get the sound working on breezy you have to use alien to convert the suse 9.3 rpm package. That's the version you have to install.
3) It's installed in /opt as many other programs. If you want to open from terminal easily just so a 'sudo ln -s /opt/MainActor_V5/mactor /usr/local/bin/'[/QUOTE]


Hi there,

I foolowed your instraction and I installed mainactor from Suse 9.3 rpm file using alien.
In the application menu now I have mainactor icon but when I clik on it nothing happens. I mean I can not run the application. 
I can not run the application even from the shell (/opt/MainActor_V5/mactor.

Do you have any advice?

Thank u

Andrea

---

### Post by 4ebees on 2006-07-09
Hi,

I think what you have to do is locate the file name:

mactor

which is likely in /opt/mainactor/

then either double-click the icon or, in the directory, run ./mactor

---

### Post by reuben on 2006-07-13
I set up an unofficial mainactor support forum, since mainconcept took the official one down.

[http://mainactor.flavor8.com](http://mainactor.flavor8.com)

---

### Post by ColinG on 2006-07-18
That perhaps says a lot about Main Concept :( . I'm not convinced by the product anyway, it is far too distro specific. Why can they not pqackage it like Open Office so it just runs (deb or rpm).

That said, you are to be commended on your initiative - MainActor needs a support group.

Colin

---

### Post by P_Badger on 2006-09-25
Well, after having spent a few days playing around wih as many Video Editing apps as possible, I have to say Mainactor is probably the best one. I WANT to like Cinelerra, but it's too crash-prone, and the ui isn't very good. Cinelerra crashes if you look at it wrong, actually.

The only problem I found with MA is that if I have "smart render" activated, MA will give me an error message saying how it "can't render picture to output file" or something like that. I'm guessing it might have something to do with using the cruddy Intel onboard graphics. With it off, the output file is still very sharp, though.

Edit: Oops, turns out the .deb version, 5.5.7, crashes when you select the "2D text" plugin. So basically, you can't put titles on the video.

---

