---
title: "Diablo rpg look and feel"
date: 2006-10-11
forum: Gaming &amp; Leisure
---

### Post by emar82 on 2006-10-11
Hello all, I recently completely switched from windows to ubuntu linux and I am very happy. The only down side for me and to others I am sure is lack of support for many good games. I know there are great games for linux however, I am just trying to find them. 

I recently tried Battle for Wesnoth and I'm addicted, I think this is one of the best turn-based strategy games around. However, What I am looking for now is a good Diablo-like game for linux. My girlfriend misses diablo and wine failed to work for me. First, I had a problem getting the game to run off the cd through wine to later find out it's due to wine not being able to emulate windows copy protection? I may be wrong here. I then tried some NOCD hacks but they didn't work either. So, does anyone know of a rpg similar to diablo for linux? Preferebly free? I have seen Neverwinter nights but was hoping to find a non-commercial great rpg. By the way, I have checked the native linux games page but could not find any rpg games she liked although I thought nethack gnome was pretty interesting. So, any diablo look and feel rpg games? :/ If not, I will need to install windows on another partition but was hoping to avoid this completely. Thanks a lot for reading!

---

### Post by Gannin on 2006-10-11
Welcome to Ubuntu.

There's a page over on winehq.com that might be of some help.

[http://appdb.winehq.org/appview.php?iVersionId=3498](http://appdb.winehq.org/appview.php?iVersionId=3498)

---

### Post by Naegling23 on 2006-10-11
I'm unaware of any diablo type games (action/rpg) on linux.  I've been running diablo2 under wine, and it runs great, I dont have any problems with the game, or over battle.net.  Neverwinter nights is also a great game, and it is available for only 20 bucks with the original game plus three expansion packs (diamond edition), so value wise, its def. worth it.  I will warn you though, its more rpg, and less action.  From the screenshots, it looks like diablo, but its a much deaper game, and the action is a lot slower.  (If you like the weapons and armor, and char. creation in diablo, then nwn is for you, if you like the action, and the fighting, then it might not be what your looking for).  

I think if I were you, I would play around in wine, and try to get diablo working, it should play just fine.

---

### Post by MrBlond83 on 2006-10-11
I'll second that Neverwinter Nights is an excellent, excellent game. The Diamond edition is indeed available cheap, and it's the original game + expansions and will provide you with a LOT of playing hours.

It is more RPGish than Diablo, but I think once you get used to it, it's an incredible game. Also, as far as I know, the game company has online expansions to the game that can be bought through their website, although I haven't tried it so I'm not sure how fun they are and if it's worth your dollar.

If you don't mind spending $20 I think it's a very worthwhile investment as far as linux gaming is concerned, and I'm sure you will not regret it if you love RPGs.

If you do get the Diamond edition, I used these instructions in order to install it:

[http://nwn.bioware.com/forums/viewtopic.html?topic=469853&forum=72]("http://nwn.bioware.com/forums/viewtopic.html?topic=469853&forum=72")

---

### Post by cezdeville on 2006-10-11
hey!

probably you've got problems with Diablo because of drives settings. you should start Wine Configuration by typing: “winecfg” in terminal. then chose “Drives”, use “Autodetect”, and then mark your cd-rom drive and choose: show advanced. it's probably set as hdd drive, change it to cd-rom and save those settings. Wine should be also set to emulate win2k.

that should solve your problems with Diablo2. for me it works perfectly (battle.net as well).

Neverwinter Nights it's also very good recommendation. those two are my favourite. i think you should also check Savage. you can download it for free from Savage home page. it's not exactly what you're looking for, but it's nice too!

Good Luck!

---

### Post by MrBlond83 on 2006-10-11
A little thread hijacking:

I am having trouble with Diablo II (without LoD) on Wine.
Two main problems:

When I choose Direct3D: DirectDraw HAL, the game runs sluggishly. In DirectDraw (2D) it runs reasonably but is very ugly.

Sound: I have picked ALSA driver in winecfg, and the sound in Diablo 2 is choppy and have small delay which is annoying.

Is there any way to fix these problems? I tend to think it's mendable due to all the reports of D2 running perfectly on Wine. By the way I installed the latest patch.

---

### Post by Naegling23 on 2006-10-11
do you have your video card drivers (not the ones supplied with ubuntu, but the nvidia or ati ones)?

Your not running in xgl are you?  Games hate xgl, use xorg.

---

### Post by cezdeville on 2006-10-11
sorry for misleading you. i'm playing Diablo2 with Direct Draw (2D) option. i should mark, that only then it runs perfectly.
for me it's sufficient, i've played 2D version on windows as well and couldn't tell much difference.
unfortunately i cannot help you with that problem.

cheers!

---

### Post by MrBlond83 on 2006-10-11
> **Naegling23 said:**
> do you have your video card drivers (not the ones supplied with ubuntu, but the nvidia or ati ones)?

Your not running in xgl are you?  Games hate xgl, use xorg.

Yeah I have fglrx installed and not using xgl.

The game works reasonably in 2d. The sound still gets choppy sometimes and it has a delay (like after you click a button a second passes by and then you hear the sound).

Other than that it seems okay. When I said the game looks ugly it must be just because I forgot it was made in 1999 :)

---

### Post by emar82 on 2006-10-11
Thanks everyone for the replies! I'm going to try to configure wine for my current cd drive problem and also check out nwn, it seems pretty awesome. Thanks again.

EDIT: Awesome! wine config was exactly the problem! This is great but just one tiny problem. When I start Diablo II my ubuntu top and bottom panels are showing in the game? :O Any ideas? I guess I can autohide but it's weird.


Another edit.. interesting, if I set my resolution to 640x480 I don't have that gfx problem.

---

### Post by Sandlst on 2006-10-12
> **MrBlond83 said:**
> A little thread hijacking:

I am having trouble with Diablo II (without LoD) on Wine.
Two main problems:

When I choose Direct3D: DirectDraw HAL, the game runs sluggishly. In DirectDraw (2D) it runs reasonably but is very ugly.

Sound: I have picked ALSA driver in winecfg, and the sound in Diablo 2 is choppy and have small delay which is annoying.

Is there any way to fix these problems? I tend to think it's mendable due to all the reports of D2 running perfectly on Wine. By the way I installed the latest patch.

I dont really know enough to help you with the video problems, but under the audio tab in winecfg, try playing around with the options Hardware Acceleration, Default sample Rate and Default Bits Per Sample, just learn what sounds best by trial and error.  I had the same choppy sound in many games through wine, and was able to fix it by changing these settings around.

---

