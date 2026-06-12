---
title: "Neverwinter Nights"
date: 2006-08-26
forum: Gaming &amp; Leisure
---

### Post by mipstien on 2006-08-26
I have done searching for nearly 3 days now and i can not find anything that is of help. first problem was that my screen was locking up and then i would have to hard reset my computer, then after it rebooted it would then reboot itself. i got nwn to run one time after i took out ./lib: from the SH file. but after i looked through the option's within the game and clicked ok it shut down the computer again and will not work again. i am lost as to what i should even try anymore, i am using NWN diamond and have used every installer out there and tried to install it from a fully updated working windows installation also.
my thoughts where that maybe it is a SDL or Lib problem but i don't know how to go about fixing this.
i also have the same similar problem loading up ut2k4. but not sure that they have anything to do with each other.
I have attempted to remove one of my Video cards thinking it was a SLI problem. but sli isn't even enabled on my computer. im not sure how to even view an error in this case because it resets before i can see anything

Ubuntu 6.06 Dapper Drake 32 bit install
3500 AMD 64
1 gig dual channel corsair XMS
Dual 6600 GT PCIE
2- 320 gig sata HD's
DFI SLI-DR mobo

---

### Post by leech on 2006-08-26
I would check several things.  It doesn't sound like it's Neverwinter Nights' problem, but more of a system problem.  How stable is it playing other 3D games?  If I were to hazard a guess, it would be bad memory.  Try using memtest86.  Could also be something wrong with your video card.  If memtest86 shows that your memory is ok, then I'd pop out your graphics card and re-seat it (obviously while your computer is off.  I don't want someone frying their computer because they thought I meant when it was on :D)

Good luck.

Leech

---

### Post by lzydba on 2006-08-26
For what it's worth, on my Slackware build having UT2004 and NWN installed at the same time caused me all kinds of problems similar to what you are describing. I never was able to figure out why. It made no sense. Istalled by themselves both games were rock solid, but as soon as I installed both either one or the other or both would go all squirelly on me.

So now on Ubuntu I haven't even tried to install them side by side, I just have NWN.

---

### Post by mipstien on 2006-08-26
well i have done single installs of every game i have :P
i can play nwn through WINE but not with the 1.67 patch installed, windows patch obviously. i can play World of Warcraft newest patch if i use D3D i have played it with openGL but only occasionally does it work for some reason. i have never really tried to get ut2k4 working just installed and it didnt work so i said whatever. Warcraft3 runs perfect in wine and so does HL2/HL1. i did have problems with the sound drivers but im not sure that would affect anything like this, cause i have tried to disable sound, not sure if i accomplished it though. i have run memtest before and it was fine before, maybe its bad now :\. everything i have runs perfect in windows with SLI. but it may just be a hardware problem, i hope not tho :(

---

### Post by mipstien on 2006-08-26
*cry* i have a bad stick of memory
corsair dual channel XMS 3200 ram, im goin to test out the 'bad' stick by itself and see if its bad alone or just in pair, and then start testing out different slots.... im praying i just need to relax a settings or something

i have a Venice AMD processor so maybe i can find something about that out there, but all my games work with the 'good' ram in just fine.

---

### Post by leech on 2006-08-27
That sucks, but on the one hand it's bad, on the other hand, we may have found your problem, which means it'll be easier to find the solution.

Could very well be that it's just your bios settings, I know Linux is a bit pickier when it comes to overclocking.

Leech

---

### Post by mipstien on 2006-08-27
im not currently overclocked 
if i have it in 1,3 slots it works at least one time to boot nwn and when i exit out if i immediatly restart nwn it crashes. if i give it time to wipe ram, 1+ minutes of doin nothin i can boot nwn again. in 2,4 it doesn't allow me to play nwn even once. i have them in slots 1,2 right now and it works, so as long as im not in dual channel it seems to work fine. i updated bios and it still isn't working correctly. i have tried other settings in bios and nothing seems to work correctly yet.... at least its working even if its not with dual channel... im goin to try my wifes ram cause its the same stuff.

---

### Post by lzydba on 2006-08-27
Even though you are not overclocking just now you might try to check this site:

[http://www.dfi-street.com/forum/index.php](http://www.dfi-street.com/forum/index.php)

I have the DFI Ultra-d and I found a lot of help there. There is tons of great indepth info on RAM troubleshooting. My board hated Corsair memory, and gave me nothing but troubles, so I ended up switching to OCZ and havent had a problem since. My system has been up 24/7 with a +800MHz overclock for over a year now.

---

