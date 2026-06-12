---
title: "KDE too slow. Any alternative?"
date: 2010-10-07
forum: Desktop Environments
---

### Post by jurco on 2010-10-07
Hi guys.

I have installed KUBUNTU 10.04 some months ago and I after couple fightings I can say it is working fine. But I am limited by the speed of KDE (4.4), everything takes couple seconds to open. Even resizing window is choppy (with all effects turned off).

Now I am thinking (please help me with these questions).
[B]1. Do I speed up my computer with installing gnome instead of KDE?
2. If I install gnome will I have new entries in my menu? (once I had gnome and I installed KDE, the menu got filled with all the K-staff).
3. Or should I just buy more RAM? How much is enough (to have nice effects and not choppy basic windows moves?
[/B]

Reasons why I like KDE - looks nice, I like the menu in the left bottom.
What I do not like on Gnome is top and bottom panel on the desktop and menu divided into 3 parts.


*I have AMD Athlon 64 4800+, 1GB RAM, Asus EAH2400 probably 128MB.*

---

### Post by viralmeme on 2010-10-07
> **jurco said:**
> I have installed KUBUNTU 10.04 some months ago and I after couple fightings I can say it is working fine. But I am limited by the speed of KDE
Try [Lubuntu]("http://lubuntu.net/")

---

### Post by Simian Man on 2010-10-07
KDE and Gnome are fairly similar in requirements.  What kind of computer do you have?  I think Xfce may be a good choice.  It is quicker than Gnome or KDE and really at least as nice as Gnome in my opinion.

---

### Post by Frogs Hair on 2010-10-07
Gnome will allow you to move the menu if you choose . I have experienced choppy window movement in Gnome only because of the video driver. I installed the Nvidia 173.xx  driver instead of 195.xx driver but I don't know  what hardware you are using.

---

### Post by kelt65 on 2010-10-07
> **jurco said:**
> 
1. Do I speed up my computer with installing gnome instead of KDE?

No, not really.

> 
2. If I install gnome will I have new entries in my menu? (once I had gnome and I installed KDE, the menu got filled with all the K-staff).

No, the menus get populated regardless of what desktop you use.

> 
3. Or should I just buy more RAM? How much is enough (to have nice effects and not choppy basic windows moves?

Yes, 1GB is very little to run a desktop on these days.

> 
Reasons why I like KDE - looks nice, I like the menu in the left bottom.
What I do not like on Gnome is top and bottom panel on the desktop and menu divided into 3 parts.

You can move the panels or menus about or delete them as it suits you in either GNOME or KDE.

---

### Post by 3Miro on 2010-10-07
1. Depending on the hardware that you have, Ubuntu may be much faster than Kubuntu. Kubuntu flies on my desktop, but is very choppy on my laptop. Ubuntu is good on both.

2. For a computer with low amount of RAM, Xubuntu and Lubuntu are both better choices. I have great experience with XFCE (Xubuntu) and definitely recommend it. It will lack a few features compared to Gnome and KDE, but it will more than pay for itself in speed.

3. Installing Gnome on top of KDE will clutter the menu and it will require that you manually change the entries (if you don't want to see them all). There may be some issues with which applications is considered "default", Dolphin vs Nautilus, Dragoon vs Totem, Amarok vs Rhythmbox and so on.

4. You can move panels and rearrange applets in both KDE and Gnome to get one looking like the other. If you install XFCE it also comes with a lower left menu by default (that is xfce4 not xubuntu-desktop, which is tweaked to look like Gnome). I have one Gnome setup where I made it look very much like windows, it is hard to notice the difference at a glance.

5. When it comes to RAM, Linux is smart. It will try to utilize as much as you have to its fullest potential (windows hogs too much of it and wastes the rest). Basically the more you have the better. Since money is always an issue, to find out how much you need, check with the system monitor during typical or heavy computer use, add RAM + SWAP and it will be nice to have at least that much.

6. RAM may not be the only issue, sometimes it is more a matter of the CPU or Video. If graphics is choppy, it is probably not RAM issue, but graphics or CPU. Let me guess, you have an old ATI video card.

7. I hope this covers it.

---

### Post by snowpine on 2010-10-07
Let us know what kind of video card you have; it is possible that simply installing the correct driver will solve the problem.

A lot of people like LXDE as a sort of "KDE-lite" desktop environment, it is certainly worth a try (and you can easily install it from the Ubuntu Software Center, then switch between KDE and LXDE from your login screen to compare the differences). :)

---

### Post by inobe on 2010-10-07
i would like to know what exactly is too slow, tell us what programs are slow ?

---

### Post by Dustin2128 on 2010-10-07
> **kelt65 said:**
> 
Yes, 1GB is very little to run a desktop on these days.

No, actually its plenty enough to run a nice KDE system, even with compositing; provided you have a decent CPU and graphics card.

That said, fluxbox or openbox would be the winners in low resource usage; I idle at 47MB RAM usage with flux.

---

### Post by Gaygerbil on 2010-10-07
Lxde uses half the ram that Xcfe uses I believe. Or around that much.

---

### Post by 3Miro on 2010-10-07
> **Gaygerbil said:**
> Lxde uses half the ram that Xcfe uses I believe. Or around that much.

RAM usage with no apps running does tell you something about the system, but not nearly as much as you would think. Almost everything in Linux is split into .so libraries, which are then shared across different programs. DE by itself doesn't do anything, everything important is in one application or another (Chromium, Firefox, Rhythmbox, Totem ... ). If XFCE uses more RAM that happens to be associated with libraries that are used by an application that I am using anyway, it makes no difference, since LXDE will have to load the corresponding libraries as well. Check the system under normal use, open browser tabs/file managers/media players and whatever else you usually use and then check the RAM usage. I don't think there will be really significant difference between different DE (assuming  you are using native apps, KDE apps do hog resources under Gnome). Then there are apps like chromium that really hogs RAM, if you have plenty, you don't care and chromium does come with speed, however, if you have limited RAM, it may be an issue.

As far as overall RAM usage I don't think you will notice difference between XFCE and LXDE.  Gnome may be a bit behind, but not by much. Most of it will be associated with compiz. Depending on the amount of effects running KDE might be worse than all the others, but not unreasonably so. XFCE and LXDE will beat other DE, but this is also due to the different set of default applications (for example Thunar is definitely lighter than Nautilus or Dolphin).

I was right about the old ATI card. KDE has some issues with ATI. Switching to XFCE and/or LXDE and probably even Gnome should help a lot. Also, make sure to try with and without the proprietary driver, ATI sometimes gives better performance for regular use with the default driver.

---

### Post by jurco on 2010-10-08
I tried to turn off/on kwin effects and that doesnt help much. At last I installed ATI proprietary drivers. Speed didnt change (for me not noticably) and the only plus is that I have nice ATI Catalyst control center for administration of my graphic card. I got also a big minus. Computer starts with composition (kwin effects) off and when if I want to use them I have to turn them on manually.

And installing ATI prop. drivers didnt get my nonchoppy resizing. Is there anybody with kubuntu nonchoppy window resizing? I think my hardware configuration is not so bad. ATI HD 2400 256MB, AMD XP 64 4800+, 1 GB RAM (ok I admit that RAM is on lower level but this shouldnt be question of RAM amount)

---

### Post by jurco on 2010-10-08
I tried to turn off/on kwin effects and that doesnt help much. At last I installed ATI proprietary drivers. Speed didnt change (for me not noticably) and the only plus is that I have nice ATI Catalyst control center for administration of my graphic card. I got also a big minus. Computer starts with composition (kwin effects) off and when if I want to use them I have to turn them on manually.

And installing ATI prop. drivers didnt get my nonchoppy resizing. Is there anybody with kubuntu nonchoppy window resizing? I think my hardware configuration is not so bad. ATI HD 2400 256MB, AMD XP 64 4800+, 1 GB RAM (ok I admit that RAM is on lower level but this shouldnt be question of RAM amount)

---

### Post by 3Miro on 2010-10-08
> **jurco said:**
> I tried to turn off/on kwin effects and that doesnt help much. At last I installed ATI proprietary drivers. Speed didnt change (for me not noticably) and the only plus is that I have nice ATI Catalyst control center for administration of my graphic card. I got also a big minus. Computer starts with composition (kwin effects) off and when if I want to use them I have to turn them on manually.

And installing ATI prop. drivers didnt get my nonchoppy resizing. Is there anybody with kubuntu nonchoppy window resizing? I think my hardware configuration is not so bad. ATI HD 2400 256MB, AMD XP 64 4800+, 1 GB RAM (ok I admit that RAM is on lower level but this shouldnt be question of RAM amount)

This is not the case of bad hardware, it is the case of bad drivers. It used to be the case that ATI will not have any Linux support. Since ADM took over, things have changed, however, you still get issues with older cards (naturally they are putting almost all of their effort towards new cards). If you can change to a newer ATI or Nvidia (or even Intel) you will see day and night difference. Also, KDE seems to be particularly picky when it comes to the bad driver, other DE will work better.

You can install XFCE and LXDE along side KDE. This will mean extra apps in the menu, but it will give you a chance to test all of the environments to see what you like.

---

### Post by cascade9 on 2010-10-08
> **kelt65 said:**
> 
Yes, 1GB is very little to run a desktop on these days.


Like Dustin2128 said, 1GB is plently. More RAM is always nicer, but 1GB should be enough, even for KDE4.X. 

I've found that KDE4.X is video card dependant. It ran better on a Athlon 2200+, 512MB, 6600GT setup than it did on a 2200+, 1GB GF4 Ti 4200 setup for me. Perfromance was acceptable on the 6600GT/512MB setup, it lagged more with more RAM and a worse video card. That wasnt kubuntu though (IIRC kubuntu, like ubuntu/xubuntu is a bit more resource hungry than some other distros running the same DE).

*edit- That could also be, well, not so much a 'bad' drivers but could well be showing differences between the nvidia 195.xx drivers and the nvidia 96.xx drivers.

---

### Post by inobe on 2010-10-08
the double post indicates a very slow internet connection.

---

### Post by jurco on 2010-10-13
inobe I wrote the double post not from home, i.e. not from the computer I was talking about :) Anyway speed of internet connection has nothing to do with speed of KDE - I think.

But for all I have a message - I switched to ubuntu and I will stay with gnome. It is much more faster even with using nice compiz effects. I wanted to uninstall kde completly, but KDE has nice krusader and kdenlive which I am used to work with. Maybe I will find an alternative :)

---

### Post by 3Miro on 2010-10-13
You can use any KDE software under Gnome, it will only take a bit longer to load and it will take more memory. Other than that, Gnome has plenty of software for all kinds of tasks, look around for alternatives.

---

