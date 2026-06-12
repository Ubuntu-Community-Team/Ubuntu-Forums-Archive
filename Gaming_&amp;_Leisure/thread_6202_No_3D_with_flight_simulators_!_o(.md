---
title: "No 3D with flight simulators ! :o("
date: 2004-11-25
forum: Gaming &amp; Leisure
---

### Post by troutrou on 2004-11-25
I don't understand.  My video card is an ATI Rage 128 Pro with 32MB, and it seems Ubuntu was great and enabled 3D and Open GL without even me asking, which is great considering all the talk on here about more modern "Radeon" ATI boards which need to be looked after apparently.

I first tried with the game 'foobillard', just because I was sure it was designed to use 3D and OpenGL. Well, it works fine, great graphics and refresh rates.

However when I start "Flightgear", it's extremely slow, one picture every 20 seconds or so, and using 90% CPU time, couldn't even access the menus. So I had to 'kill' it. Sadly I looked in the man page, and there is no 'debug' option available.

Same problem with another flight simulator "Search and Rescue" (found in Synpatic universe). If someone could try this game and tell me what happens on his machine, I would be very grateful.
On this game, 3D again is clearly not working, as you can see from the attached screenshot ! Very 'blocky' indeed. It uses 95% CPU time too, so no doubt it's not using the video card at all... :-/
Thank god, this game DOES have a debug option, and here is what it says (see text file for full debug text)

"Search and Rescue requires an alpha channel, current alpha channel is 0 bits in size.".

Looking at debug info, it seems that a thing called "glX" is having problems with "single" and "double" "buffers" that are not available.

Any clue ? 


Regards,

Vince.

---

### Post by BWF89 on 2004-11-26
You must fly model airplanes, cool. Same as my dad...

---

### Post by troutrou on 2004-11-26
[QUOTE=BWF89]You must fly model airplanes, cool. Same as my dad...[/QUOTE]

I beg your pardon ? 

No I don't fly model airplanes, what did I say that led you to believe this ?? I am lost...

Vince

---

### Post by BWF89 on 2004-11-26
You said you were having trouble with your "flight simulater". Most of the people who fly model airplanes have flight simulaters on their computers. I thought you meant you were having trouble with the real kind. Not the play kind. My mistake...

This is a real fight simulater. The joysick you get is the same as the controle you use to fly time airplane in real life
[IMG]http://store1.yimg.com/I/rc-models_1822_266218582[/IMG]
[http://www.rcmodels.com/rc-dav-rcfs-2001.html](http://www.rcmodels.com/rc-dav-rcfs-2001.html)

But that's the new kind. The one we have is so old it runs almost entirely in MS Dos. You can really see the jaggies when you are flying the plane...

---

### Post by troutrou on 2004-11-27
> You said you were having trouble with your "flight simulater". 

Yes, "Flightgear" and "SearchAndRescue", as I specified... but maybe you didn't read my post properly ?! ;o)

> Most of the people who fly model airplanes have flight simulaters on their computers. I thought you meant you were having trouble with the real kind. Not the play kind. My mistake...This is a real fight simulater. The joysick you get is the same as the controle you use to fly time airplane in real life
[http://www.rcmodels.com/rc-dav-rcfs-2001.html](http://www.rcmodels.com/rc-dav-rcfs-2001.html)

Although this is getting off-topic and I would rather receive help on my glX problem to get the game working... I would admit that I do have interest in R/C helicopters, but sadly I don't like any of what is available on the market. They are too small and not realistic enough to my taste. I do have dreams of building a realistic Bell 222/230 model about 3 meter long, but this will requires lots of time and engineering...and money. So it's not going to happen anytime soon.
The biggest complain I have about available helicopter models is that they mostly are toys, even with a 4 stroke engine it still sounds crap and produce lots smoke, and the 'joystick'/remote control, are plain rubbish. How can people fly a heli with these toy remote controls ? I wonder. 
And about this "simulator" software you are refering too, it hardly a real simulator, I am afraid it's apparently  (according to decription on the site) purely designed to simulate the R/C models, not the real, full scale thing. Real Helis physics models is what I am looking for, and the only one I know with real physics models for Heli...is the famous "Microsoft Flight Simulator". Sadly it doesn't work in Linux, which is why I was trying to get 'Flightgear' to work, as it seems it is also designed with realistic physics in mind. So I would have liked to try it.

So, back to the beginning : please can someone help with my 'glX alpha channel' problem.... :o(

Vince.

---

### Post by theh0g on 2004-12-01
Dude, the best fligh sim out there (physics, ...) is available on Linux...it's called X-plane. Read: [http://www.linux-gamers.net/modules/news/article.php?storyid=573](http://www.linux-gamers.net/modules/news/article.php?storyid=573)

---

### Post by troutrou on 2004-12-03
[QUOTE=theh0g]Dude, the best fligh sim out there (physics, ...) is available on Linux...it's called X-plane. Read: [http://www.linux-gamers.net/modules/news/article.php?storyid=573](http://www.linux-gamers.net/modules/news/article.php?storyid=573)[/QUOTE]

Thanks for the link ! Just had a look at the game's website. Wow, what can I say, it looks and sounds perfect in every respect. Beautiful graphics, truly realistic physics, it has Helicopters in it, you can download more helis, you can make your own, and it looks like it could just about run on my machine (Athlon XP 1.45Ghz + 512MB of RAM and ATI 128 Rage Pro 32MB).
It's not free but price is affordalbe given the superbe quality of the game, it is worth it. Also, the guy focuses on rendereing of american town, but I am more interested in EUropean cities, so I hope the game can cope with European buildings whose architecture is somewhat more diverse and complex thant american concrete blocks...

So I will wait for the game to be mature (developpe says the graphics quality is still under heavy developpment and should be a lot better very soon ! :-), then just buy a copy  ! :o)
In the meantime, I will try and download the ++++MB of the demo version, should take about a day.... I don't have broadband.... :-/

Thanks you so very much for the link !! :o)


Vince

---

### Post by theh0g on 2004-12-05
[QUOTE=troutrou]Thanks for the link ! Just had a look at the game's website. Wow, what can I say, it looks and sounds perfect in every respect. Beautiful graphics, truly realistic physics, it has Helicopters in it, you can download more helis, you can make your own, and it looks like it could just about run on my machine (Athlon XP 1.45Ghz + 512MB of RAM and ATI 128 Rage Pro 32MB).
It's not free but price is affordalbe given the superbe quality of the game, it is worth it. Also, the guy focuses on rendereing of american town, but I am more interested in EUropean cities, so I hope the game can cope with European buildings whose architecture is somewhat more diverse and complex thant american concrete blocks...

So I will wait for the game to be mature (developpe says the graphics quality is still under heavy developpment and should be a lot better very soon ! :-), then just buy a copy  ! :o)
In the meantime, I will try and download the ++++MB of the demo version, should take about a day.... I don't have broadband.... :-/

Thanks you so very much for the link !! :o)


Vince[/QUOTE]
 I've tried id also,  I have Athlon 1700xp, 256MB ram and GF4 4200. Runs perfect on 1024x786, very fast and smooth, too bad it isn't fullscreen and too bad it stops working after 5 minutes. I've always admired this game on Windows, it really is great. I hope you like it.

---

