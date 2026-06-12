---
title: "No Screen With Wubi"
date: 2008-12-03
forum: General Help
---

### Post by neversmileatacrocodile on 2008-12-03
I install Wubi, reboot, and after choosing Ubuntu from Grub it boots into a black screen, and nothing happens. :/ I think my hardware isn't supported.

I have an Acer Extensa 4630Z laptop, currently running Windows Vista. 9.9 If I can get a small Ubuntu partition on this laptop that would be nice, but right now it doesn't look promising.

---

### Post by Jammanuser on 2008-12-03
> **neversmileatacrocodile said:**
>  If I can get a small Ubuntu partition on this laptop that would be nice, but right now it doesn't look promising.

huh? are u saying that ur trying to install wubi on a separate partition than Vista??? don't do that!!! wubi installs ubuntu as a regular Windows app, on ur Windows partition, and so u don't need a separate partition to install wubi on!

-jammanuser

:D

P.S. personally, i think u would be better off installing ubuntu on a separate partition, WITHOUT using wubi...and just eliminate the wubi idea altogether!!! i happened to use wubi to install ubuntu 8.10 on top of Vista (just like ur trying to do!), and after about a week, i could no longer boot into ubuntu anymore, due to a "crc error" and then on next line "system halted" message...and i've STILL not got it fixed! Cheers! ;)

---

### Post by OneSeventeen on 2008-12-03
For me, I had to enter the ubuntu menu after choosing ubuntu from the Windows Boot Manager, and choose safe graphics mode, or something similar.

(the first boot I just had a black screen because it was attempting an obscure refresh rate my monitor didn't understand)

After it installed and rebooted, I let it boot into ubuntu like normal and all is well. :)

Not sure if that is the same problem, but I hope it helps.

---

### Post by Jammanuser on 2008-12-04
> **OneSeventeen said:**
> For me, I had to enter the ubuntu menu after choosing ubuntu from the Windows Boot Manager, and choose safe graphics mode, or something similar.

(the first boot I just had a black screen because it was attempting an obscure refresh rate my monitor didn't understand)

After it installed and rebooted, I let it boot into ubuntu like normal and all is well. :)

Not sure if that is the same problem, but I hope it helps.

and was that doing a **proper** install of wubi, i.e. installing on TOP of ur Windows OS, on the same partition? ;)

somehow i have a feeling that it was... xD

Cheers!

-jammanuser

:D

---

### Post by neversmileatacrocodile on 2008-12-04
Nononononono! I haven't done any partitions! I used Wubi from inside windows! If WUBI works THEN I'll try partitioning and putting Ubuntu on.

But I can't even get to an Ububtu screen of any kind. I choose 'Ubuntu' from the Grub window and the screen goes black. There's no choice for safe graphics mode or anything.

My monitor is just not compatible I guess.

---

### Post by Jammanuser on 2008-12-04
> **neversmileatacrocodile said:**
> Nononononono! I haven't done any partitions! I used Wubi from inside windows! If WUBI works THEN I'll try partitioning and putting Ubuntu on.

But I can't even get to an Ububtu screen of any kind. I choose 'Ubuntu' from the Grub window and the screen goes black. There's no choice for safe graphics mode or anything.

My monitor is just not compatible I guess.

ok...well that checks that possibility off! i'm sorry that i can't be of any further help, but i have literally **no idea** what could be the problem with ur screen...i would suggest trying a different monitor, to see if it works then! other than that, i'm all out of suggestions! ;) Good luck with ur problem!

Cheers! :)

-jammanuser

:D

EDIT: oh! sorry! i forgot that urs is a laptop...so trying a different monitor is probably not an option for u then...unless of course u want to connect a regular monitor to ur laptop, which is possible! Cheers!

---

### Post by tarps87 on 2008-12-04
It is highly unlikely to be a monitor problem, it is more likely a graphics problem.
Is there any hard drive activity after this screen?
Usually after selecting Ubuntu you should see a second screen with boot options, this is run with the same 'graphic settings' as the first screen. To may need to press the escape key at the first screen, I have not used wubi much so will give it a go when I get home.
If there is no hard drive activity I would try reinstalling it as assuming it is a new install you have nothing to lose

---

### Post by neversmileatacrocodile on 2008-12-06
Woot! I reinstalled and tried again and this time everything loaded up fine and I could install. Before I couldn't get to any sort of graphical install window mode or Grub, I would click Ubuntu from the OS choice screen and then the screen would just go blank. But this is working now.

That being said, I may never use Ubuntu fully over Windows. I have too many Windows only requirements, but having Ubuntu on this laptop to play with means I don't have to worry, I have it there if I need a break from a Windows World.

Thanks guys!

---

### Post by Jammanuser on 2008-12-06
> **neversmileatacrocodile said:**
> Woot! I reinstalled and tried again and this time everything loaded up fine and I could install. Before I couldn't get to any sort of graphical install window mode or Grub, I would click Ubuntu from the OS choice screen and then the screen would just go blank. But this is working now.

That being said, I may never use Ubuntu fully over Windows. I have too many Windows only requirements, but having Ubuntu on this laptop to play with means I don't have to worry, I have it there if I need a break from a Windows World.

Thanks guys!

Cool...i'm glad that u got it working! :D But I wasn't suggesting that u give up Windows altogether...for most of us, that is simply not an option right now, for there r too many programs that we depend on that run only on Windows! What i was suggesting was, that if u have any plans of using Ubuntu a lot...u should install it on a separate partition, rather than using Wubi! I personally have had a "crc error" after about a week of having Wubi installed...after which i could no longer boot into Ubuntu! Just just fyi...for long term use, its better to install Ubuntu on a separate partition! ;)

Cheers! :)

-jammanuser

:D

---

