---
title: "Has anybody got The Sims to work?"
date: 2006-09-09
forum: Gaming &amp; Leisure
---

### Post by NiceGuy on 2006-09-09
Hey there all, I was just wondering if anybody has gotten The Sims (the first one) to work on ubuntu?

For some reason I have a craving to play it (last month it was Transport Tycoon :roll:). Most sources seem to say that it doesn't work but a few say that transgaming made a version for Mandrake a while back.

I'm already signed up for cedega but I was wondering if a) the 'windows version' works (either by wine or cedega) or b) if not then can I use the Mandrake version with ubuntu?

I've already sent an email to transgaming but am still waiting on a reply so in the mean time I thought I'd ask here,

Mark B-)

---

### Post by haxer on 2006-09-09
It would probably work with wine but wine sux for 3d games so no .... im also probably going to sign up for cedega so i can play steam :P hmm.. but try looking att google.com serch for the sims+install+linux 0r sims+ubuntu :)

---

### Post by NiceGuy on 2006-09-09
.

---

### Post by NiceGuy on 2006-09-09
I've googled loads and come up with nothing concrete. That's why I was asking here. The best anyone can say is it 'should' work or 'it works under mandrake'. Looks like I'll just have to go for the mandrake version and hope :(

---

### Post by haxer on 2006-09-09
Hmm... yes try it and then post how you downloaded it and how you did :) it would be great to know :)

---

### Post by Cynical on 2006-09-09
According to their database, The Sims 2 doesn't play very well but the mandrake edition does. I would try to get that if I were you.

[http://transgaming.org/gamesdb/games/view.mhtml?game_id=3284](http://transgaming.org/gamesdb/games/view.mhtml?game_id=3284)
[http://transgaming.org/gamesdb/games/view.mhtml?game_id=2324](http://transgaming.org/gamesdb/games/view.mhtml?game_id=2324)

---

### Post by NiceGuy on 2006-09-09
I think that's the way forward... and it seems that ebay is the only way to get hold of it. I just hope that its easy to install, ie. it comes on a separate disk and not integrated into the os. 

I don't want to have to install the OS just to play the game!

---

### Post by slugkilla on 2006-09-09
I use to be obsessed with The Sims when I used windows. I can conferm that the very first version does not work on ubuntu. I Also have tried the Double Delux version with it's exspansions. I think I actually got it to install once but could not get it to play. I really hope that someone getts this working on ubuntu some day.

---

### Post by NiceGuy on 2006-09-10
Did you try using cedega or just wine?

---

### Post by NiceGuy on 2006-09-19
Well the Mandrake Gaming version of the sims arrived today and I'm pleased to report that its working just fine!

For anyone who's interested this is what I did to get it working (you probably won't need to do all these steps but this is EXACTLY what I did):

1. Copy the 3 .rpm packages (sims.rpm, simsdata.rpm, winexsim.rpm) found on the cd to home folder.
2. Install 'alien' from synaptic (for thoes who don't know this is a rpm to deb converter).
3. Open up a console and type:
```
sudo alien sims.rpm
```
then
```
sudo alien simsdata.rpm
```
(you may get chmod errors - I just ignored them) then
```
sudo alien winexsim.rpm
```
4. Install your 3 new generated .debs
5. Type the_sims into a console and find that it doesn't work :(
6. Go to [http://www.transgaming.com/register_sims.php](http://www.transgaming.com/register_sims.php) and register your copy of the sims.
7. Go to [http://www.transgaming.com/webstore_download_update.php](http://www.transgaming.com/webstore_download_update.php) and type in your cd key again and then download both The_Sims-3.2-1.i386.rpm and WineX_Sims-3.2-2.i386.rpm to home folder.
8. Open up a console and type:
```
sudo alien The_Sims-3.2-1.i386.rpm
```
then
```
sudo alien WineX_Sims-3.2-2.i386.rpm
```
9. Install your two new debs which should over right the ones on the CD.
10. Open up a console and type the_sims and follow on screen instructions. Enjoy!

---

### Post by haxer on 2006-09-19
Omg sound like a lot of trouble to get the sims to work nee im happy with Drugwars <Synaptic>Search>Drug>Install>Enjoy 
Truecombat elite <[http://Katanoon.nl/Ubu-e](http://Katanoon.nl/Ubu-e) 


All you need :) \\:D/ :rolleyes: \\:D/

---

