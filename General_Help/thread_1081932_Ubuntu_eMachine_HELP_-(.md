---
title: "Ubuntu eMachine HELP :-("
date: 2009-02-27
forum: General Help
---

### Post by Maxx730 on 2009-02-27
Hi, 

I have used Ubuntu 8.04 on my 1.4 Ghz Dell D600 for a while now and everything works great and is VERY fast.  My friend got a new desktop and gave me this old 1.6 Ghz eMachine Desktop with around 600mb of RAM on it. I decided to install Ubuntu and it runs alright but I expected it to be a lot faster.

The only difference between this computer and my laptop is that my laptop has 2Gb of RAM. If I buy more RAM for the eMachine will it run any faster? Or will it not make much of a difference? 

Any help would be much appreciated!

Thank You
God Bless

---

### Post by Peter09 on 2009-02-27
How much Ram have you got? If you run HTOP it will show you how much memory and swap you are using. If you are using a lot of Swap (more disk access) then memory may help.

Sorry just seen that you have 600MB - which should be OK.

---

### Post by Maxx730 on 2009-02-27
yeah I thought 600Mb would be fine, and it works, the problem is when i minimize and maximize windows it laggy loading the windows and I need to do work on this computer so I dont know if buying like a gig of ram will be worth it or not.

O and the video card is 32mb AGP which I dont know if that would make any difference.

---

### Post by Peter09 on 2009-02-27
Yeah, I would guess your video card will be one of the things that will affect graphic performance, if you have a good card in one and not in the other you may well see the difference.

Try making the windows as simple as possible, no effects etc.

---

### Post by Maxx730 on 2009-02-27
yeah I have all the settings off, but its still kinda slow. what kind and size video card would you suggest if I were to buy on. Im kinda on a budget so I only need what I can get by with because I dont mind not having compiz fusion on this computer

---

### Post by Peter09 on 2009-02-27
You could try a less demanding interface such as XFCE. You should be able to install that ontop of the system you have now. It would allow you to judge if it is the graphics card, and you could switch between the two window managers.

try
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

I do wonder though, really the spec of your machine should be adequate. The other option is to upgrade to the (Still in Alpha) jaunty which is quite sprightly.

---

### Post by Maxx730 on 2009-02-27
Well, I went all around trying to find a 64 or even 128mb graphics card and could not. So im stuck with 2 32mb graphics cards. If I put both in will it make any difference?

Also thanks for all the help.

---

### Post by mpsii on 2009-02-27
eBay is your friend for cheap 128MB cards... find an ATI X1300 or X700 and you will find heaven.

---

### Post by Maxx730 on 2009-03-01
Well I ordered a 256mb ATI graphics card off of ebay. So I am hoping that that will make everything better. It seems as though the computer is not slow because it doesnt hinder how fast the programs run, it just looks slow because the graphics take a lot of time to catch up.

---

### Post by Maxx730 on 2009-03-06
Alright,

I got the 256mb Graphics card and installed it into my computer.  When I start up ubuntu the only thing that happens is the whole screen is orange with squigally lines in between every so often.  Then I can move a part of the orange which I think is supposed to be the mouse cursor.  Is the Graphics Card too powerful for the computer? Or is it not getting enough power?

PLEASE HELP :(

---

### Post by abn91c on 2009-03-06
> **Maxx730 said:**
> Alright,

I got the 256mb Graphics card and installed it into my computer.  When I start up ubuntu the only thing that happens is the whole screen is orange with squigally lines in between every so often.  Then I can move a part of the orange which I think is supposed to be the mouse cursor.  Is the Graphics Card too powerful for the computer? Or is it not getting enough power?

PLEASE HELP :(
try going to recovery mode, the new card may not like compiz, turn off desktop efects in recovery mode you may need to remove compiz also to get in.```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

---

### Post by Maxx730 on 2009-03-06
Here is my problem though, I dont have to choice to go into recovery mode. The only thing I see when I start my computer is that orange screen and thats it, no other graphics.  Is there something I might need to install before I put the new graphics card in?

---

### Post by Maxx730 on 2009-03-06
Also I talked to a guy at Best Buy about a week ago and he said that I shouldnt get a high end graphics card for this computer because it wouldnt have enough power to supply the graphics card.  But I dont think 256mb is highend, maybe im wrong.

---

### Post by abn91c on 2009-03-06
> **Maxx730 said:**
> Here is my problem though, I dont have to choice to go into recovery mode. The only thing I see when I start my computer is that orange screen and thats it, no other graphics.  Is there something I might need to install before I put the new graphics card in?
at the orange screen do [COLOR="Red"]**ctrl+alt+f1**[/COLOR] to get to a command prompt

---

### Post by Maxx730 on 2009-03-06
Here is a link to a video i made of what happens when i start up the computer with the graphics card in it. For some reason there is no sound and it is sped up, but you still can see what happens when it starts up.

[http://www.Maxx730Designs.com/thenew/0002.ogg](http://www.Maxx730Designs.com/thenew/0002.ogg)

---

