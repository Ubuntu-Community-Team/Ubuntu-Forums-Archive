---
title: "My whole system freezes - Jaunty"
date: 2009-04-29
forum: General Help
---

### Post by Ascenti0n on 2009-04-29
Both yesterday and now this morning, I have had to restart my PC via the on/off power button, as the WHOLE system freezes up.

My suspicions is that it may be something to do with Firefox, perhaps flash?

**I wrote the following in a post yesterday:**
I did have a panic earlier today though as I had my system froze quite often and had to restart my machine each time. I tried looking at the server logs but I don't know what I'm looking for.

I suspected it was an add-on for Firefox. So I un-installed completely from within Synaptic, manually moved the .mozilla file elsewhere and then reloaded Firefox, and all seemed to be stable again.

I don't think it's add-ons within FF, and I'm only 90% convinced it has something to do with FF.

Can anyone shed some light as I use my machine all day for work as well as r&r.

---

### Post by lyn james on 2009-04-29
I also have a similar problem.

Hardware is Dell Dimension 521 dual core 4600+ with  Nvidia Geoforce 7300 LE

Upgraded to Jaunty yesterday, and have had 3 hangs since then, (no response to mouse or keyboard)  which can only be recovered by a power cycle.The system is therefore unusable. 

Assuming it may stay up long enough, how could I revert back to the Intrepid kernel without having to re-install?

Help anyone?

---

### Post by Ascenti0n on 2009-04-29
After I posted this thread, I saw another with the same issues. It seems that Complete system freezing is quite common, and may be nothing to do with Firefox.

Most fingers are wagging at EXT4 or the current kernel build.

---

### Post by rhy7s on 2009-04-29
Getting a bunch of freezes, but the repeatable one is when the blank screen saver comes on. If the screen comes back again it flashes on and off continuously quite quickly with the cursor frozen and no response to keyboard input.

---

### Post by purbeck on 2009-04-29
> **Ascenti0n said:**
> After I posted this thread, I saw another with the same issues. It seems that Complete system freezing is quite common, and may be nothing to do with Firefox.

Most fingers are wagging at EXT4 or the current kernel build.

Not just a Ububtu thing either - I've just moved from openSuse 11.1 for exactly the same reasons - and I'd tested four different browsers, three KDE releases, GNOME and fvwm but still had sudden total locks. It's definitely not a Firefox issue, and I'd agree that current kernel or X are the most likely culprits. But there's never anything in the logs to help diagnostics. Problems only started when I upgraded from Suse 10.3 to 11, and didn't go away when 11.1 came out.

Surprisingly, since installing Jaunty I've not had a single freeze. Fingers crossed.....

---

### Post by Ascenti0n on 2009-04-29
> **rhy7s said:**
>  it flashes on and off continuously quite quickly with the cursor frozen and no response to keyboard input.

Thats exactly the symptoms I had yesterday, the screen flickers rapidly with screwed up graphics and no keyboard or mouse input. That's why I initially suspected firefox.

---

### Post by bailout on 2009-04-29
> **Ascenti0n said:**
> 
Most fingers are wagging at EXT4 or the current kernel build.

I have had it once on kubuntu 9.04 running on ext3. I had assumed it was kde4 or kubuntu bugginess.

---

### Post by mdgo80 on 2009-04-30
> **Ascenti0n said:**
> Both yesterday and now this morning, I have had to restart my PC via the on/off power button, as the WHOLE system freezes up.

My suspicions is that it may be something to do with Firefox, perhaps flash?

**I wrote the following in a post yesterday:**
I did have a panic earlier today though as I had my system froze quite often and had to restart my machine each time. I tried looking at the server logs but I don't know what I'm looking for.

I suspected it was an add-on for Firefox. So I un-installed completely from within Synaptic, manually moved the .mozilla file elsewhere and then reloaded Firefox, and all seemed to be stable again.

I don't think it's add-ons within FF, and I'm only 90% convinced it has something to do with FF.

Can anyone shed some light as I use my machine all day for work as well as r&r.

Are you having issues with Flash videos like Youtube?? I was having troubles with the scroll bar and some flash bases sites. I used the info [in this thread]("http://ubuntuforums.org/showthread.php?p=7182393#post7182393") and actually my flash issues were solved. I hope it stop the freezing too. In my case everything looks just normal, i can move the mouse but i can't click anything.

---

### Post by manuelb on 2009-04-30
> **lyn james said:**
> I also have a similar problem.

Hardware is Dell Dimension 521 dual core 4600+ with  Nvidia Geoforce 7300 LE

Upgraded to Jaunty yesterday, and have had 3 hangs since then, (no response to mouse or keyboard)  which can only be recovered by a power cycle.The system is therefore unusable. 

Assuming it may stay up long enough, how could I revert back to the Intrepid kernel without having to re-install?

Help anyone?

I've your very same machine but i switched the video card to an nVidia GeForce 9400GT, but i never experienced this type of complete lookups, just the "strace gedit" problem as of [here]("http://ubuntuforums.org/showthread.php?t=1129414").

---

### Post by ArduinoFun on 2009-04-30
Same thing happened to me yesterday. I couldnt do anything. I finally managed to reinstall ubuntu by using tap and enter keys. Even after I reinstalled, the left click on my touch pad would not work. If I plugged in a mouse it would. Then after about 3 hours of the reinstall. My left click started working again. I thought the system was froze because I couldnt click to open anything. It turned out that it was just the left click wasnt working. I dont know how it started working again though.

---

### Post by 4Orbs on 2009-04-30
When I was using ext4, I could reproduce the freeze most any time by deleting a bunch of large files then immediately emptying the trash. I'm on ext3 now, until ext4 is bulletproof.

---

### Post by xRes on 2009-04-30
I had this issue on fresh install of Jaunty also. My system CPU frequency was slightly overclocked (which ran without issue before), reduced that, problem solved.

---

### Post by pbarclay on 2009-06-12
Hi,

I found this problem was down to the NVidea display Driver from Nvidea- if you uninstall it then you won't get the freezing.

I say this because I did a fresh install of Ubuntu 9.04 and everything worked flawlessly until I attempted to install the Nvidia Driver using EnvyNG. 

The system would randomly Freeze, I could not ssh into it or do anything. Had to reboot using the power switch. It only appears to freeze with Firefox, but it will do it at any time.

After removing the driver everything works fine again.

I found a number of articles for this, try searching for "7300LE Nvidea freezing ubuntu"

I am still searching for a solution to the problem but at least I know what it is now.

I hope this helps.

I have a Dell E521 system with a GeForce 7300LE graphics card.

---

