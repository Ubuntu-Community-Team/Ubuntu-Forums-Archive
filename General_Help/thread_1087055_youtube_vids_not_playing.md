---
title: "youtube vids not playing"
date: 2009-03-04
forum: General Help
---

### Post by Pacopag on 2009-03-04
Hi.  I used to watch youtube vids all the time without any problems.  Now when I click one, I get a black rectangle where the video should be playing, and nothing else happens.

Anyone know what's going on?

---

### Post by connorh123 on 2009-03-04
I have the same problem, however, mine is just a gray arrow and it doesn't play when I click on it.  I've heard rumors that the new Ubuntu update allows Ubuntu users to now watch videos.  I've also heard that Google is working on a program for Linux called "Google Chrome", which also allows you to view videos.

---

### Post by C-- on 2009-03-04
Do you remember making any changes to your system recently?

Do you have the latest version of flash player installed?

---

### Post by Pacopag on 2009-03-04
I don't remember changing anything lately.  I don't usually mess with configs.  But I do always get all of the security/recommended updates.  Maybe a recent update screwed it up?

---

### Post by Kemon on 2009-03-04
I just reinstalled ubuntu 8.10 today. I think I have the same problem.
When I'm watching on youtube, I can't see every vids, sometime I get a grey window. Then I can refresh or go back, then forward and then the vid will play again.
Installed the newes today I thing :(

---

### Post by Pacopag on 2009-03-04
I checked out some other websites that use flash and I get the same thing...a black rectangle where the flash should be.

Maybe I'm getting black where others are getting gray because I am using a dark desktop theme.

---

### Post by Pacopag on 2009-03-04
clicking "back" or "refresh" doesn't work either.

---

### Post by Kemon on 2009-03-04
I just got a screen shot of it:
[IMG]http://img4.imageshack.us/img4/6051/youtubeflash.jpg[/IMG]
I can hear the sound, but I can't see anything. A few frefreshes help sometimes if not, I have to restart firefox

---

### Post by Therion on 2009-03-04
Starting with something simple and easy open Synaptic and search for/install **ubuntu-restricted-extras** and see if that installs/upgrades any packages and solves the problem.  

If still no joy we'll try bigger guns.



**EDIT:**

Ugh...   What was I thinking??  Don't use Synaptic, use apt-get:```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Kemon on 2009-03-04
Still grey. :(

---

### Post by Therion on 2009-03-04
Open Synaptic.  
Search on "Gnash". 
Remove any Gnash-related packages you find.
Log out, log back in.
Try YouTube.
Report back with joy.

---

### Post by RedSingularity on 2009-03-04
I was having the same problem but as mentioned above 
"sudo apt-get install ubuntu-restricted-extras" fixed it for me.

---

### Post by Kemon on 2009-03-05
What to do then?

---

### Post by PrateekParekh on 2009-03-05
How about removing and re-installing Flash?

Does the same happen on other browsers like Epiphany?

---

### Post by connorh123 on 2009-03-07
Once I did that Sudo command, I tried running youtube and seeing if it was any different. It was, slightly. However, when I tried running Counter-Strike, the font was bigger. What did I do wrong?

---

### Post by Noack on 2009-03-08
hey i have some problems too, i cant see youtube videos, and mi counter strike with wine begins but then the screen puts black and i need toreestart mi computer!!

---

### Post by dskotl on 2009-03-08
I am running ubuntu 8.10  and I did have the same problem. I know the way I fixed it was uninstalling flashplayer  which I had version 9.0 and there is a 10.0 out now so if you have the old version or just ran the update, it didnt fix mine I had to uninstall the old and install the new.

---

### Post by GrfyGrumpyBear on 2009-03-09
that happened to me, just upgrade flash through synaptic with all browsers closed, fixed

---

