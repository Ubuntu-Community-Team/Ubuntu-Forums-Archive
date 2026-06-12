---
title: "Cedega vs Wine for Halflife2"
date: 2006-10-12
forum: Gaming &amp; Leisure
---

### Post by tristan on 2006-10-12
I've been using wine with various degrees of success for running windows games lately. I managed to get Halflife 2 (GOTY DVD version) up and running with pretty good framerates. A bit of reading around suggested that Cedega had better DirectX support and would run HL2 with a bit more graphic prettiness, so I splashed the US $55 for a year subscription (I'm happy to support commercial linux software, your philosophies may vary).

I've actually done the two HL2 installs side by side under wine 0.9.22 and Cedega 5.2.6, and have done a few comparisons which might interest people.

Both programs run HL2 at roughly equivalent framerates, perfectly playable at 1024x768 with settings on low (I have a 2.6Ghz P4, 1G RAM, 6600GT). 

Cedega's DirectX support is indeed better than Wine's at this point. DirectX 8 features like bump mapping and shadows work. Water effects are better under cedega, but no amount of fiddling with shader settings will get true water reflections happening.

Neither program will properly behave if I force DirectX 9 when launching HL2 - as soon as I change any graphic settings it just drops back to DirectX 7.

I get occasional nasty graphic glitches such as textures which disappear when I look at them, but reappear when I turn away. This is very apparent in the Combine Bridge section, where the bridge girders you need to navigate are invisible. Dropping back to DX7 fixes this. This is a reasonably well known bug with the current Nvidia drivers, but neither Nvidia nor Cedega will put their hands up to fix it

Wine allows Steam to log on in 10 seconds, it takes 2-3 minutes under Cedega. This is extremely annoying.

Wine loads HL2 in 1/2 the time Cedega does. This is also annoying.

At this point in time I'm tending towards Cedega just because of the better DX8 implementation, despite the annoying login and loading slowness and occasional graphic glitches. It will be interesting to see how soon it takes Wine to improve their DirectX...

---

### Post by Hmarroqu on 2006-10-12
I tried installing halflife with wine...it worked but dint....the game freaks out ...perhaps there is something i have to do other than install it with wine and run it..?  

how did u get HL2 to work if i may ask?:neutral:

---

### Post by Doctoxic on 2006-10-13
Hi

I am also having problems to get HL2 to run under Wine (though i am running Edgy, so it might just be that).

Anyway, i winder if i am missing some steps - what i have done is:

1) Installed Steam under wine 0.9.22 with no problems.  It installed fine and i did NOT follow all the other steps described here <<http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wine&back=HOWTO+INDEX+Wine>> because i think that with the latest Wine you don't need to.

2) Half Life 1 and TFC both run fine through Steam.

3) My sound is Alsa - i tried changing to OSS in winecfg but it made no difference.

4) So i can start HL2 through steam and get to the new/load/option/etc screen.  However if i start a new game the introductory video (rise and shine Mr Freeman) doesn't play, i do hear the voice but it is very jerky.

4) In Steam i don't have anything in the 'Launch Options'.

If anyone has HL2 working under Wine did you do anything different?

Many thanks


Doc

---

### Post by bastiegast on 2006-10-13
Nice to read, its exactly the experience I had: wine loads fast, cedega has the nice graphics(and loads slowww)

---

