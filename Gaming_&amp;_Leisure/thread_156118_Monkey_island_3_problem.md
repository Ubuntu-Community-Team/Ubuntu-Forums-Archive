---
title: "Monkey island 3 problem"
date: 2006-04-06
forum: Gaming &amp; Leisure
---

### Post by ClubShewty on 2006-04-06
okay I decided to play again a classic game, the curse of monkey island. I am running it with cedega. Install and all goes fine untill I am trying to play the game.  I click the "play" switch and then there pops directX installer and whatever I do in that point, I cant go playing. It just go back to launcher, so what's the problem? :confused:

---

### Post by glaze on 2006-04-07
It should work with ScummVM.

---

### Post by deathbyswiftwind on 2006-04-20
sweet glad to see another monkey island fan! ill find my copies and try to install under cedega and tell ya my results

---

### Post by fng on 2006-04-20
Yep, you should try to play it in scummvm instead of cedega/wine.

---

### Post by Miguel on 2006-04-21
Like everyone else said, forget about wine/cedega. I have played Curse of Monkey Island only once, and that was on ubuntu breezy...  under scummvm. Just install scummvm from the ubuntu repositories and go to /usr/share/doc/scummvm. There should be a document explaining how to install CoMI and how scummvm works.

BTW: be ready to ditch 1Gb of hard disk space, you must copy the whole data of the 2 CD's to play CoMI.

2nd BTW: All lucasarts adventures up to grim fandango (this one excluded) work in scummvm. Broken Sword also works in scummvm, but you must download the media files from scummvm.org, as the team was asked not to reverse-engineer miles sound system.

3rd BTW: To get sound you will probably have to "killall esd" before launching scumm vm.

---

### Post by Claus7 on 2008-03-25
Hello,

I was trying to play The Curse of Monkey island (the third instalment in the series) on Ubuntu Dapper Drake 6.06. I had wine and crossover and I had all the files of the game on my hard disk. I was doing right click on the COMI.exe file, trying to open it with one of the above, yet to no avail due to this error log:

 [COLOR="DarkOrange"]unable to load resource\font0.nut[/COLOR]

I have to say that this problem isn't faced only by linux users, yet by windows users as well. The solution to this problem was to use the scummvm program.
I downloaded it from the repos and I opened it from Applications->Games->ScummVM. 

Then this was a tricky part, at least for me:
Click the option 'add game' on the right and navigate on the left in order to find the folder of the game you want to play. Click it only once so as to mark the folder of the game. Then click 'choose' and the game should be added to the scumm's list. And you are ready to play!

This is a link on how to add games in scumm VM:
[http://www.youtube.com/watch?v=fveeuMNBumc&feature=related](http://www.youtube.com/watch?v=fveeuMNBumc&feature=related)

And this is a link with compatible games with it:
[http://en.wikipedia.org/wiki/ScummVM#Games_supported_by_ScummVM](http://en.wikipedia.org/wiki/ScummVM#Games_supported_by_ScummVM)

Regards!

---

