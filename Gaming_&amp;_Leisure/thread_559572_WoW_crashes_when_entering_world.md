---
title: "WoW crashes when entering world"
date: 2007-09-25
forum: Gaming &amp; Leisure
---

### Post by allizzle on 2007-09-25
i looked everywhere for people with the same problem and found some 
but no solutions to it, when i choose a character it loads and then just stays there OR freezes up my computer ending up in a restart, what do i do?

---

### Post by allizzle on 2007-09-25
bump

---

### Post by hikaricore on 2007-09-25
What video hardware are you using?  Which driver are you running for it?
Is WoW in opengl or d3d mode?  Provide as much info as possible if you want assistance.

---

### Post by allizzle on 2007-09-25
well, i tried both opengl and d3d, im using ati x1300 thats all i know

now for some reason it crashes at retrieving character list

---

### Post by Faud on 2007-09-25
> **allizzle said:**
> well, i tried both opengl and d3d, im using ati x1300 thats all i know

now for some reason it crashes at retrieving character list


Not to sound sarcastic but has it worked before ? Im asking because they are doing patch 2.2.0 as Im typing this and servers and not fully up.
Could that be a possibilty.

PS...My comment is from a US standpoint.. Dont know about the servers for our friends in Europe

---

### Post by allizzle on 2007-09-25
it has not worked before but my friends are online right now so the servers are definetly up

also i tried opengl and d3d both one more time, turns out when im in d3d it freezes at retrieving character list, but when im in opengl i get online for 0.5 seconds and then it freezes my computer and i have to reboot

---

### Post by hikaricore on 2007-09-25
I'm not an ATI expert by any means, but if you're using a supported ATI card, you'll need to install the proprietary ATI drivers.

Just so you know ATI is currently improving it's drivers for Linux users which have been terrible up until recently, but they are still far from the best.

---

### Post by allizzle on 2007-09-25
where would i find drivers for it ive looked around but cant find any,

also i managed to stay on for about 30 seconds and then bam, frozen

---

### Post by Ghost|BTFH on 2007-09-25
It's an issue with the new patch. They added VoIP into the mix so people could use voice chat in game.

The problem is, it's not fully supported via WINE.

For a temporary fix, disable all sound in WINE by opening a shell and typing:

winecfg
(hit enter)

And clicking on the Audio tab (this will take a few moments for it to switch) and uncheck anything checked in there.

I'm currently having a similar problem where it refuses to fully load, or it takes forever to load and then finally disconnects me. However, turning off all sound = I pop right into the game, no issues.

This tells me the issue is obviously with the new patches mucking around with sound.

The fix? I don't know. Anyone out there smart enough to figure it out? :)

I'm running ALSA, no ESD or OSS for me.

Cheers,
Ghost|BTFH

---

### Post by allizzle on 2007-09-25
tried that didnt work, i dont think the voice chat in game is even in EU yet

---

### Post by Pikestaff on 2007-09-25
> **Ghost|BTFH said:**
> It's an issue with the new patch. They added VoIP into the mix so people could use voice chat in game.

The problem is, it's not fully supported via WINE.

For a temporary fix, disable all sound in WINE by opening a shell and typing:

winecfg
(hit enter)

And clicking on the Audio tab (this will take a few moments for it to switch) and uncheck anything checked in there.

I'm currently having a similar problem where it refuses to fully load, or it takes forever to load and then finally disconnects me. However, turning off all sound = I pop right into the game, no issues.

This tells me the issue is obviously with the new patches mucking around with sound.

The fix? I don't know. Anyone out there smart enough to figure it out? :)

I'm running ALSA, no ESD or OSS for me.

Cheers,
Ghost|BTFH

Thanks!  This got me into WoW, the new patch made it impossible for me to get me into the game; disabling all the sound works.  Granted I'll be sad to not have sound for a while but I think I can live, and hopefully we'll see a fix soon.

Now to figure out some of the errors I'm having with my add-ons... :p

---

### Post by epdp14 on 2007-09-25
I have also noticed that WoW no longer saves session data...

I have to re-agree to the ToS every time I start WoW, in addition to reactivating all of my out-of-date addons.

Anyone else having this problem? Any suggestions?

Thanks

---

### Post by Pikestaff on 2007-09-25
As another update to the sound issue with the new patch, I have noticed that using ALSA won't let me log in, but OSS seems to work fine.  Although I prefer ALSA to OSS myself, as it works better for me overall (and lets me have out-of-game music and in-game SFX), in this case it seems to be a viable alternative, at least until a fix for ALSA gets sorted out.

I am having the same problem epdp14, with having to re-agree to the ToS and re-enable my addons.  I seem to recall this happening previously though, and a fix for it, perhaps we can find it...

**Edit:** Maybe try [this post]("http://ubuntuforums.org/showpost.php?p=2708253&postcount=41").

**Edit Again:** The post I linked to worked for me.  Got past the ToS and kept my add-on settings.

---

### Post by epdp14 on 2007-09-25
Worked perfectly! :guitar: Thanks!

---

### Post by allizzle on 2007-09-25
but back on my problem... :p

nothings worked so far

---

### Post by igster on 2007-09-25
I was getting incredibly bad framerates after the patch so I switched from ALSA to OSS in winecfg as was mentioned here and it did the trick.  The sound is nowhere near as accurate and dynamic set to OSS but I can deal with it until there's a real fix.

---

### Post by allizzle on 2007-09-28
bump please help me

---

