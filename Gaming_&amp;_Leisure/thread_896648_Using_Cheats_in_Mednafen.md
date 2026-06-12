---
title: "Using Cheats in Mednafen"
date: 2008-08-21
forum: Gaming &amp; Leisure
---

### Post by bentzilla on 2008-08-21
Hi, 
I have been using the mednafen emulator for a while and it works great (much better than visual boy advance, which had choppy sound) and i have been wondering how to use action replay/code breaker cheats. I have searched and searched for help on this but have found no guide on how to add these cheats. Help on this matter would be much appreciated.

Thanks,

Bentzilla

---

### Post by FranMichaels on 2008-08-21
I like to make my own codes for fun, but anyway
when in mednafen, press alt + c and from there is self explanatory. 
A little menu comes up with numbers, 1 being add cheat, etc...
Press alt + c when you are done.

alt + t toggles cheats on/off

---

### Post by bentzilla on 2008-08-21
Thank you, I'll look into that more. (I found a page on that [Here]("http://mednafen.sourceforge.net/documentation/cheat.html"))
How would i go about converting action replay/code breaker codes? I have been looking at making .cht files, which i believe mednafen uses. I found [This Guide]("http://www.m3wiki.com/index.php/GBA_Cht"). Am i on the right track? Thanks for your help.

---

### Post by FranMichaels on 2008-08-21
Yes, you are on the right track there. The only thing is that editing the .cht file by hand can be a little tricky, you must keep the formatting. I'll post an example of some (using the alt + c method does add them to the .cht file upon exit.)

```
[182363b0698322e1864ced6e9eed7ead] 1207 - MegaMan Zero 2 (U)
R A 1 L 0 02037d84 0d Invincible

R I 1 L 0 02036bc0 0a Freeze play time

R I 2 L 0 02037eee 03e8 Crystals

R A 1 L 0 02036bb5 06 S rating
```

So for the codes you want to add, prefix it with R A 1 L 0, that "stuff" is whether it replaces the value, the byte length, etc. Standard codes should fall into that... The rom file title as well as checksum is included in the cht files mednafen makes. Just play around a bit you should be fine once you get the hang of it.

---

### Post by bentzilla on 2008-08-22
Okay, I've been messing around with the Alt-C method and I'm getting used to it, however it takes a long time to find what I want and there are certain things I don't think is possible with this method. For example, I'm playing Pokemon - Fire Red and lets say I want all the Pokeballs. This I believe is only possible with action replay.
So this is the code:
```
Have All Pokeballs
a81e2fc0
3988f7b1
2dafd739
5d796510
```
Now, Thats a big code, so for messing around I've been trying to get this 2 line code to work (and I could probably figure this one out with the Alt-C method after a good amount of time). Since its smaller I figured it would be easier to trial and error with.
```
Infinite Money
29c78059
96542194
```
So that being the original Action replay code I tried using some of the guide on [COLOR="Red"][This Page]("http://www.m3wiki.com/index.php/GBA_Cht")[/COLOR] to convert the codes to raw format (I also have a Windows Machine). By doing so
```
Infinite Money
29c78059
96542194
```
becomes
```
Infinite Money
042257BC
000F423F
```
Then after converting to .dat file and renaming to .cht it becomes
```
[Infinite Money]
ON=020257BC,000F423F
```

So then I thought
```
[Infinite Money]
ON=[COLOR="Red"]020257BC[/COLOR],000F423F
```
Is the address, and 
```
[Infinite Money]
ON=020257BC,[COLOR="Red"]000F423F[/COLOR]
```
Is the value. So in my .cht file I have
```
R I 1 L 0 020257BC 000F423F Infinite Money
```
Which does not work.  I have also tried changing the code to things like this
```
R I [COLOR="Red"]5[/COLOR] L 0 020257BC [COLOR="Red"]F423F[/COLOR] Infinite Money
```
Thinking that the 5 is the byte length and after reading the previous mentioned guide to trim the extra 0's so that 5 characters remain.

If it would be possible could I have an example of converted action replay codes, or any extra help regarding this matter. And also I believe a  Master Code is **NOT** necessary, but confirmation would be great. 

Thanks,

Bentzilla

---

### Post by FranMichaels on 2008-08-23
You do not need master codes AFAIK with emulators :KS. 

I didn't know some AR codes are encrypted (they look weird, as normal codes are some address with some value) 

> 
Datel as of now has encrypted the codes on the Action Replay for PS2, GC and GBA; this was meant to stop hackers from translating its codes for use in other cheating devices, but it prevents users from making their own codes for their games.
[http://en.wikipedia.org/wiki/Action_Replay](http://en.wikipedia.org/wiki/Action_Replay)

Anything is possible with the alt + c method, including multi byte codes, and entering things in hex. You just have to pinpoint a value in memory to change.

Here is a code I made, and an example of the formatting style

gedit ~/.mednafen/cheats/gba.cht

Put it right under the [md5sum hash]title of your pokemon game
(note the space between each line)
```

R A 1 L 0 02023d50 ff Battle EXP

R A 2 L 0 0203993c 0000 Shop Items Free

R A 3 L 0 02000490 00000000000f423f Infinite Money

```

Toggle it on and off with alt+t, otherwise your pokemon will level up forever after a battle.

I'll make some cheats or convert some if I find something usable...

The infinite money code you made is valid, just the wrong byte length. The thing is it just doesn't work... 

Notice the codes I've made, the value isn't too far off from the code you converted. Perhaps there is some sort of offset (like subtract 200 from the address...)

EDIT: Okay, I got it, code I made works, it turns out one has to buy/sell something before the game shows the money (best to toggle it on/off, it has graphic glitches if you leave it enabled all the time...)

The offset, if it is consistent, would mean that the address of each code you convert
subtract 2532C (hex)

To clarify, 020257BC - 0002532C = 02000490 (again all hex, left the extra zeros to make it easy)

It is 3 bytes. F423F is hexadecimal for 999999 (aesthetically pleasing for infinite money, no?)

Anyway, 
1 byte = 256
2 bytes = 65536
3 bytes = 16777216

However, since counting from 0, and those who have played Zelda 1 for NES, Link can hold 255 (FF in hex) rupees. So when dealing with values, subtract 1.

---

### Post by bentzilla on 2008-08-25
Thank you so much for your help. For the moment I think I'll leave the action replay codes as they are tricky and require a lot of fiddling around with. 
You mentioned that anything is possible with the Alt-C method. I was wondering if you could teach me how to use this method. Things such as how you pinpoint the exact address and what values are needed. I would really like to learn that method. If that is possible then that would be great.

Thanks again,

Bentzilla

---

### Post by FranMichaels on 2008-08-25
Basically you use the menu for values that have changed, greater or less than, or equal. You narrow down the results then play with the values. 

You just have to think like the game.

In Super Mario bros. when mario is hurt, he flashes for a bit, and is invulnerable. There is a timer value that is decreasing, pinpoint it, and make it last. There is likely a flag (0 or 1) that is triggered as well. 

For RPGs, searching for values is a good way. Also looking at adjacent bytes, as things like hp and mp may be next to each other.

For things like key items, an old technique (bitmasking) may be used to save memory. For example, let's say there are 8 key items, that can be picked up at different times. You could store all the values in one byte.

(in binary, 8 bits is 1 byte)
Let's say you've got the first and last item
10000001 (129 in decimal)
00110000 (48 in decimal)

Get it? So searching for lesser or greater may be misleading in that case.

So to get all item setting the value to FF (or 255)
11111111

Other things are locations, like in rpg, there may be a value which points to the world - room, whatever. The best way to narrow down some of these changes is via save states.

It may seem a bit dry, but I enjoy making cheat codes as a simple mental exercise. Try a game with numeric values and toy around. Sometimes there are also 2 identical values. For example, one might be the time, and the other the same value drawn on the screen. Change the latter, and the timer may still run out. Change the other and you are all set.

---

### Post by bentzilla on 2008-08-25
Okay, so I have been messing around on Pokemon Fire Red with the Alt-C method. So, just to try it out I tried Infinite Health/Max Health w/e. So, The Pokemon was hurt a bit, 73/79 health. Then I used the search for values of 73. Then I used a potion, thus fully restoring health to 79/79. Then using the values increased search feature I received 4 results. 2 of which are what I'm looking for. So, I make the selection type in the name, byte length (which lets say for full health I want 999/79, hehe. So I believe, and am not entirely sure on this, but, it should be 1 byte.) Then I type in the value 999. This same process goes for the second search result (Asuming one is for graphical and one is the actually value). Okay so far so good, I activate cheats, and the Pokemon's health is 231/79? So, into a battle I go. It is impossible to die (health gets to 0, then resets to 231 the next turn.) The issue is if i use a potion, then the health just keeps increasing and never stopping, resulting in having to reload the game. Could you please advise on this error, or add any extra tips for using the Alt-C method.

Thanks,

Bentzilla.

---

### Post by FranMichaels on 2008-08-25
It's 2 bytes.
Why use a potion on a pokemon with infinite health?
The error is odd though, if you want to share the codes I'll play with it.

2 results. try setting the value of one or the other, it could be like I mentioned in my above post. One value for on screen value, and the true value. The potion refilling would go on forever if the other value is set...
Or, it could be to setting the wrong byte length and a high value, I'm not sure what happens in that case...

---

### Post by bentzilla on 2008-08-25
I set the byte length to 2 and the health now displays 999/79, so that is working. The Potion error is still happening though.

Edit: Instead of setting the current heath value x/79, I set the actual amount of health to 999. This is much better than what I was previously attempting because the health now becomes 999/999. You can lose health and using potions still work, but 999 is a lot of health. The only problem I found is that if you level up your stuck with 999 health. Not too bad though.

```
R A 2 L 0 020242dc 03e7 999 Health
```

This is my cheat file. (Pokemon Shiny Gold is a Fire Red Ips Patch. But Cheats Will Work the exact same as Fire Red.)

```
[cf5224ef504a2442898bab5ebb390cb9] Pokemon - Shiny Gold
R A 1 L 0 02023d50 ff Battle EXP

R A 2 L 0 0203993c 0000 Shop Items Free

R A 3 L 0 02000490 00000000000f423f Infinite Money

R A 2 L 0 02023c0c 03e7 Max Health * This is useless now that I found a better way.

R A 2 L 0 020242da 03e7 Max Health 2 * Same as above

R A 2 L 0 020242dc 03e7 999 Health

```Something weird I noticed was when I modified the cheats the default value (Instead of typing the previously entered value you can just press enter) was a ridiculous negative number? Why is this?

Edit: I asked the stupid question how do I determine Byte Length. When 1 Byte = 256. And 999 is greater than that, so obviously it is 2 Bytes. Stupid me.

I'm getting the hang of easier direct values. How would I go around looking for a no random battles. That doesn't have a specific value that I know of. You said to think like the game, so I'm thinking right now that when i step into grass it calls a code to set if I'm going to get a random battle and which Pokemon I'll be facing. This seems a really hard thing to figure out, but is it possible?

---

### Post by harrypotter123 on 2010-04-03
I don't understand. Can you tell me what everything means? Like R A 1 L 0, etc? And can it please be like I tell you a cheat name, and you tell me what to put in the Value, Bytes, etc? I want to try it on Pokemon games.............:P

---

### Post by Zedex on 2011-10-26
Hello.
I do not understand how by the code :
```
Infinite Money
29c78059
96542194
```you can get :
```
R A 3 L 0 02000490 00000000000f423f Infinite Money
```Moreover in game, when I follow instructions (alt-c, add new code, etc ...) I don't know what should I put in "Byte Lenght [1]:", and finally, I get :
```
R A 3 L 0 0000001d 0000000005c11df2 Infinite Money
```But it does not work at all.

---

### Post by Bryant.GhostInTheMachine on 2012-01-03
I just installed Mednafen and followed the steps above to enable and use the described cheats. One problem: it's not working. the console output shows 0 cheats are loaded when I start up LeafGreen. The file is set up properly (I copied and pasted it from this thread) except for a slight confusion as to the filename. You said that the file should have the game's checksum directly before the cheats, in brackets, followed by the name of the game (presumably the filename). My game is called LeafGreen.GBA, and my first line is set up as: 

```
[0x266951c2886707f3b1287db7ef6de55a] LeafGreen.GBA
```

Yet Mednafen won't load the cheats. Why?

---

### Post by Bryant.GhostInTheMachine on 2012-01-03
Sorry, I think I might have put this in the wrong thread. But, since it relates, I'll restate my problem in a concise manner. Here is my cheat file:

```
[0x266951c2886707f3b1287db7ef6de55a]  LeafGreen
R A 1 L 0 02023d50 ff Battle EXP

R A 2 L 0 0203993c 0000 Shop Items Free

R A 3 L 0 02000490 00000000000f423f Infinite Money
```

when I run mednafen and check the console output, it informs me that the cheatfile has been found but '0 cheats loaded'. This is sorely vexing. Why are the cheats not being loaded?

---

### Post by santtu1 on 2012-06-14
Anyone knows rare candy code? And how you use these codes? I don't know what I should  to do?..:/ game is Pokemon Leaf Green.

---

### Post by santtu1 on 2012-06-19
Does anyone know how to use any Game Shark codes on Mednafen? (sorry 'bout my bad english)

So please someone tell me:)

-santtu1

---

