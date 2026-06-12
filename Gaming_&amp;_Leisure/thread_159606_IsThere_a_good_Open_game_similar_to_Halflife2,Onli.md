---
title: "IsThere a good Open game similar to Halflife2,Online&amp;with Other .Net-Players?"
date: 2006-04-13
forum: Gaming &amp; Leisure
---

### Post by patrick295767 on 2006-04-13
IsThere a good Open game similar to Halflife2,Online&with Other .Net-Players?
   
The most famous open linux game  one similar to it?
  
Thank you, 

Patrick
--
I have enough of ppracer & mupen64, ... time for next level !! :-) :-D

---

### Post by gnu2tux on 2006-04-13
nexuis or cube ?

---

### Post by patrick295767 on 2006-04-13
I looked [http://www.igames.co.il/screenshots/view_list.php?Game_ID=4264](http://www.igames.co.il/screenshots/view_list.php?Game_ID=4264)
nexuis looks more like unreal tournament ... no ?
what do you think ? 
  
The motor engine of HL2 was really impressive when I had windob ... 

I am looking cube now... 

thank you !!

---

### Post by Gustav on 2006-04-13
True Combat:Elite (mod for Enemy Territory) is a great (counter-strikish) game. [http://truecombat.com](http://truecombat.com)

---

### Post by PriceChild on 2006-04-13
Unless i'm much mistaken, you can run Half Life 2 in Cedega pretty well, Not too sure about wine.

Pricey

---

### Post by patrick295767 on 2006-04-13
[QUOTE=Gustav]True Combat:Elite (mod for Enemy Territory) is a great (counter-strikish) game. [http://truecombat.com](http://truecombat.com)[/QUOTE]
  
The Graphic-Engine looks very nice when looking at the screenshots ... 
:-) 

thank you

---

### Post by william_nbg on 2006-04-13
I'd check out True Combat: Elite.

I have hf2 installed on my box via cedaga, but after finding TCE I've never gone back. It's got great graphics, and is the most realistic online shooter.

---

### Post by patrick295767 on 2006-04-13
[QUOTE=william_nbg]I'd check out True Combat: Elite.

I have hf2 installed on my box via cedaga, but after finding TCE I've never gone back. It's got great graphics, and is the most realistic online shooter.[/QUOTE]
  
Sounds good for TCE2 !!! :D 
I am curious which one has beettter graphics engine : HL2 or TCE ??
 
...

Thx for information !

---

### Post by Paulus on 2006-04-13
I havn´t played TCE, but I seriously doubt it has better graphics than HL2, with HDR an all that.  Also the physics wouldnt be near that of CSS.   I havn´t played TCE admittadly, but the HL2 engine is so critically acclaimed its hard to belive TCE could be better :/

please correct me if i am wrong!!

---

### Post by void_false on 2006-04-13
Last time I tried to play True Combat was few month ago. It didnt run because of some version conflicts or something like that. Is it working OK now?

---

### Post by william_nbg on 2006-04-14
Well, at the time of speaking, TCE 0.48 is the current version. The next version, including major updates, is due out in a few weeks. No, I don't think TCE has the graphics of HL2, TCE uses a modified Q3 engine. Though, the detail on some of the maps is damn good. And don't forget TCE is opensource, free as in free beer, while HL2 is not only comercial, but is using Steam. 

The world, and the internet could do without software like Steam. I have nothing against paying for software I really want, or like - I've donated money to the Ubuntu fondation. I just don't like someone looking over my shoulder every time I start the application.

---

### Post by Gray. on 2006-04-14
There is no game on Linux that could compare to HL2 (graphically) with the exception of Doom 3/Quake 4. That being said, graphics don't make a game and TC:E is a very fine game, except I can't find any local servers so I gave up on it. Playing with ~250 ping while everyone else is ~70-100, gets dull after a few months lol.

Steam I think is one of the best (and worst things) to happen to the games industry.
It is a great launching pad for those lesser-known titles/mods (Rag Doll Kung Fu, Darwinia, Red Orchestra etc) and helps get more money back to the developers therefore better games (hopefully), but it's still slow and the whole verification thing is lame to me. I paid for the game and activated it, is that not enough?

---

### Post by void_false on 2006-04-15
So can anybody confirm that it is now possible to play TC:E? Because I still cant connect to any server.

---

### Post by Gustav on 2006-04-18
[QUOTE=void_false]So can anybody confirm that it is now possible to play TC:E? Because I still cant connect to any server.[/QUOTE]
I play it all the time :) (never had any problems though)

---

### Post by void_false on 2006-04-18
Are you running ET 2.60 and TC:E 0.48?

---

### Post by Gustav on 2006-04-18
it's TC:E 0.48, I don't know which ET but I think it's 2.60. How do you check?

---

### Post by void_false on 2006-04-18
Press ~ to open game console. Your version will be writter in bottom right corner.

---

### Post by Gustav on 2006-04-18
Just checked, it's 2.60

---

### Post by void_false on 2006-04-19
Strange. I have same versions but everytime I try to connect to some server I recieve error saying "cannot load official pak file. plz verify your installation bla bla bla". Do you know anything about it?

---

### Post by void_false on 2006-04-22
I've deleted "tce" and "tcetest" directories from my "home" and everything suddenly started to work. ;)

---

### Post by minisori on 2006-04-24
[QUOTE=void_false]I've deleted "tce" and "tcetest" directories from my "home" and everything suddenly started to work. ;)[/QUOTE]

That was posible cause you had the tce folder with root permisions and that is why you could not download anything. It has happend to all my friends the same thing.

---

### Post by void_false on 2006-04-24
I must reveal you my secret. I'm playing as root. Shhh... ;)

---

### Post by patrick295767 on 2006-04-24
[QUOTE=void_false]I must reveal you my secret. I'm playing as root. Shhh... ;)[/QUOTE]
  
As root, Ouch ouch ! :cool: 

Try maybe a chmod oug+rw -R /gamefolder ...
It can be working ... I wish ...

Pat'

---

### Post by void_false on 2006-04-24
I will play as regular user as soon as I figure out how to make the following command execute automagically at start up. ](*,) 
```
echo "et.x86 0 0 direct" >/proc/asound/card0/pcm0p/oss
```

---

### Post by Spark* on 2006-04-24
[QUOTE=void_false]I will play as regular user as soon as I figure out how to make the following command execute automagically at start up. ](*,) 
```
echo "et.x86 0 0 direct" >/proc/asound/card0/pcm0p/oss
```[/QUOTE]

Put it into your /etc/init.d/bootmisc.sh right at the end of the do_start() block (after rm -f /tmp/.clean).

---

