---
title: "Battle for Wesnoth"
date: 2007-04-09
forum: Gaming &amp; Leisure
---

### Post by viergeame on 2007-04-09
I don't know if this is the right place for this, but I'll try anyway.  I installed Battle for Wesnoth and fell in love with it playing through the tutorial.  The problem is that I can't start a campaign.  I click the campaign button and nothing happens.  I really want to be able to play more of this game.

---

### Post by jbizz8 on 2007-04-09
Might be a daft question but have you installed the campaigns?

---

### Post by desicratn on 2007-04-09
I was in the same boat when I first installed it. 
I started downloading campaigns as I went but after 2 I just ended up downloading and compiling from source(it comes with like 9 campaigns and its the latest version too!). The guide on the website is really easy to follow. You will need to install the build essentials to compile( there are other threads about this  here too) but once you get going its a cinch.
I installed it for my kids, they love it.
happy installing

---

### Post by arron on 2007-04-10
Hope this helps, no need to compile...

```
$ apt-cache search wesnoth
wesnoth - fantasy turn-based strategy game
wesnoth-data - data files for Wesnoth
wesnoth-editor - map editor for Wesnoth
wesnoth-ei - Eastern Invasion official campaign for Wesnoth
wesnoth-httt - Heir to the Throne official campaign for Wesnoth
wesnoth-music - music files for Wesnoth
wesnoth-server - multiplayer network server for Wesnoth
wesnoth-trow - The Rise of Wesnoth official campaign for Wesnoth
wesnoth-tsg - The South Guard official campaign for Wesnoth
wesnoth-ttb - A Tale of Two Brothers official campaign for Wesnoth
wesnoth-utbs - Under the Burning Suns official campaign for Wesnoth

```

Have fun!

---

### Post by viergeame on 2007-04-11
I assume the campaigns are downloaded.  A friend of mine installed it when he installed Ubuntu for me, but I wasn't there the whole time.  He said it should work fine, but it's possible that he overlooked it because of dealing with all the other problems the computer decided to have.

---

### Post by daynah on 2007-04-11
It's easy to overlook. I installed Wesnoth twice (on my laptop and desktop) and then did  a clean install of Ubuntu on my laptop... and started screaming at Wesnoth! "Why wont you let me do a campaign?! Do I have to do the tutorial first?!" I did the tutorial and saved... no campaign. Freaking out.

Oh wait... doh! No campaigns to play. It's nice to have them seperate, I think. If you don't like the campaign, or didn't find it fun you can keep your computer clean (some of us have very little space for our gaming habits). And it also means that the home made campaigns will work just as well as the official ones. :)

(in Ubuntu (Gnome) go to Applications > Accessories > Terminal. I don't know how to get to Terminal in Kubuntu (KDE), you should be able to look around and find it in the menu somewhere. Then just type this, substituting "name of campaign" for one of the campaigns on the list.)

sudo aptitude install nameofcampaign

---

### Post by djotaku on 2007-04-15
I'm glad I read this - I was having exactly the same problem!

---

### Post by ben2talk on 2008-05-10
Haha, me too. Feel stupid now. It's a shame that the game isn't clever enough to open a list of campaigns installed instead of silently failing and appearing to simply open a new tip - looks like a fault and is rather unprofessional :-s

This kind of game is a real competitor in my mind to Windows games, such as 'Halflife'. Although we lose out on the big budget mega graphics, I think gameplay here is better. I spent more time playing games like this in my mobile than sitting playing on windows. Now I just need an excuse (like being able to run it full screen on one side of my cube...) to avoid booting windows.

---

### Post by samjh on 2008-05-10
> **ben2talk said:**
> Haha, me too. Feel stupid now. It's a shame that the game isn't clever enough to open a list of campaigns installed instead of silently failing and appearing to simply open a new tip - looks like a fault and is rather unprofessional :-sUnfortunately Battle for Wesnoth is designed to be distributed together with "mainline" campaigns.  They are an integral part of the game.

Separating the mainline campaigns from Wesnoth is like installing something like Warcraft III and then deleting the campaigns folder.  It's not how the game is meant to be used.

:)

---

