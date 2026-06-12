---
title: "Is Beryl slow?"
date: 2006-11-24
forum: Desktop Environments
---

### Post by Danyl on 2006-11-24
Hi all

I installed Beryl/emerald themes on my new Edgy Ubuntu system but it seems to be slowing down everything I do on my system.

When I boot up (Beryl auto opens) but if I open an app, it just hangs. When I close Beryl/emerald themes down, the app starts up straight away. 

Is this normal? Is it a trade off to have sweet eye candy vs normal brisk processing?

---

### Post by b1g4L on 2006-11-24
Nope. You shouldn't really notice a slow down on processing. You may be experiencing slow downs because your graphics card is old or not fast enough or the drivers are not properly installed / configured. I have Beryl/XGL running on a ATI 9800 pro and its very smooth. I don't notice any slowdowns on CPU intensive tasks.

---

### Post by rlozano on 2006-11-24
i believe beryl is very dependent on what video graphics hardware you have. if you have kinda old video graphics card or a low video ram, you will mostlikely feel the slowdown.

and yeah, you have to choose between performance or features, if your machine is quite limited in using beryl. :)

---

### Post by Danyl on 2007-02-06
I think I should have elaborated a little more on my problem. My apologies all.

When Beryl's active (set as the window manager), when I launch an app from the panel, the 'box/rectangle' graphic that flies out from the icon to signify you've opened a program, is really jerky.

Does this make sense? I'm referring to the simple animation that occurs in gnome when you open an app from the panel and that simple box shaped graphic expands to fit the screen temporarily before the splash screen of the application or application window fills your screen.

For some reason its jerky in beryl but fine when beryl is disabled.

Is this fixable?

---

### Post by irish_flu on 2007-02-06
No apologies necessary!  :)

What they're saying is that whether or not beryl is "slow" can depend on what hardware you have (as well as what drivers you're using with that hardware).

A couple of questions for you:
can you post some system specs (especially video card make/model, as well as your computer's processor speed and amount of RAM)?

Can you post a link to what directions you followed, or tell us what steps you took, to get Beryl up and running (in case some change in setup would help)?

If you're using an nvidia card, which drivers are you using?

Are you running Ubuntu Dapper (6.06), or Edgy (6.10)?

---

### Post by Spr0k3t on 2007-02-06
To me, beryl seems slow on even the fastest graphics card you can get.  If you start turning off some of the glitz/glamour/glory everything will become noticably faster.  There's only six things I have running with beryl.  Runs very crisp and no fancy animations I have to watch over and over.

**Side Note**
Not to be mean or anything, but could i get a move for this thread to Environment rather than beginner talk?  [Looking For Beryl?](http://ubuntuforums.org/showthread.php?t=349732)

---

### Post by luvinit on 2007-02-06
Last week Beryl updated itself under the usual automatic update routine. It now jerks like crazy, to the point where i have turned it off. I had never seen that before.

---

### Post by zgornel on 2007-02-06
Make sure you do not have the blurring plugin enabled. It slows beryl a lot. On my i915 is speedy (I use only transparencies and the cube, nothing else) but still has some minor focus issues.

---

### Post by mcduck on 2007-02-06
> **Danyl said:**
> I think I should have elaborated a little more on my problem. My apologies all.

When Beryl's active (set as the window manager), when I launch an app from the panel, the 'box/rectangle' graphic that flies out from the icon to signify you've opened a program, is really jerky.

Does this make sense? I'm referring to the simple animation that occurs in gnome when you open an app from the panel and that simple box shaped graphic expands to fit the screen temporarily before the splash screen of the application or application window fills your screen.

For some reason its jerky in beryl but fine when beryl is disabled.

Is this fixable?

That makes sense, and is also possible to fix.

The problem is that Gnome has animation for launching apps, and then Beryl has some too and doing those both at the same time can make things jerky. But as the Gnome's animation is ugly anyway you can just turn it off with Configuration Editor:

1. Press Alt-F2 and run 'gconf-editor'
2. Browse to apps/panel/global and deselect 'enable_animations'

You might need to log out & back again for this to take effect.

---

### Post by techno-mole on 2007-02-06
i installed beryl a few days ago and i have not noticed anything, i use wobbly windows (which i spend much time messing with) i have tried most setttings and not really noticed any slow down, all seems to be fine.
i would have thought that beryl being a very graphical program, ie lots of eye candy type stuff, then it would need a relatively powerful graphics card ? i use an nvidia ge force 7600 gs 256mb (agp) and all the graphics run really well, and if i am honest i get smoother graphics using linux than i do if i use windows.
maybe its a driver issue ?

---

### Post by zetsumei on 2007-02-06
the only slow i notice is when im using the burn effect and minimize windows, other than that no slow down for me...make sure you have the latest graphic drivers for your graphics card...

---

### Post by mcduck on 2007-02-06
> **techno-mole said:**
> 
i would have thought that beryl being a very graphical program, ie lots of eye candy type stuff, then it would need a relatively powerful graphics card ? i use an nvidia ge force 7600 gs 256mb (agp) and all the graphics run really well, and if i am honest i get smoother graphics using linux than i do if i use windows.
maybe its a driver issue ?

Actually most Beryl plugins are very simple and basic 3D stuff, and require hardly anything from your graphics card. People have reported Beryl it with cards like Geforce 2 on old computers..

Some plugins require you to have modern graphics card as they use features that older cards don't have like pixel shaders. These of course won't work on old cards. (water plugin and fdo-mode in blur need pixel shaders)

Other than that the performace is pretty much up to having good drivers for your graphics card.

---

### Post by ButtonMasher on 2007-02-06
I have had Beryl running on Haruhi (in my sig) for a couple months now and I can't say that I've seen any difference when running it.  I'll notice a couple dropped frames of animation now and then, but for the most part it runs that same as Metacity.  I've definitely never had any trouble opening windows.  Now I don't have Beryl opening automatically when I start the computer.  I type 'beryl-manager' in the terminal to get it started when I want to show off for my Windows using friends.   :)

---

### Post by jvc26 on 2007-02-06
I think it will be down to your hardware/incorrect drivers. I havent had any slowdown on the whole, but its not unheard of.
Il

---

### Post by Brunellus on 2007-02-06
thread has been moved to a more relevant forum.

---

### Post by luvinit on 2007-02-06
I have tried altering settings to see if it makes any difference, there is no speedup by removing some of the plugin options. The benchmark plugin says it is running at 60/70 frames, but it looks moire like 2 frames  a second. Unusable.

---

### Post by CheeseEatingBulldog on 2007-02-07
I thought I would pitch in seeing as I have just been messing around with beryl as well.

I successfully run AIGLX/Beryl on an AMD1300XP with a mere Geforce2 64MB card. Note that before today I was running XGL instead of AIGLX, but the beryl update to RC2 broke my setup. So I decided to switch away from XGL and go with the native built in AIGLX. I must say that it seems tht XGL was faster, and a little smoother. (this could be due to the new plugins). But will give it a while.

Does anyone even know what the performance differences are under XGL and AIGLX respectively?
Another question is, what IS the difference between Compiz and Beryl? Is Compiz more...sleek (OS X ish) and Beryl just plain eye-candy overkill?

---

### Post by Danyl on 2007-02-09
> **CheeseEatingBulldog said:**
> 
Another question is, what IS the difference between Compiz and Beryl? Is Compiz more...sleek (OS X ish) and Beryl just plain eye-candy overkill?

This is a question I am interested to know too.

And thanks for the helpful hints everyone, I will give them a try.

---

### Post by larstorben on 2007-02-26
> **mcduck said:**
> That makes sense, and is also possible to fix.

The problem is that Gnome has animation for launching apps, and then Beryl has some too and doing those both at the same time can make things jerky. But as the Gnome's animation is ugly anyway you can just turn it off with Configuration Editor:

1. Press Alt-F2 and run 'gconf-editor'
2. Browse to apps/panel/global and deselect 'enable_animations'

You might need to log out & back again for this to take effect.

Thanks! This cleared up my last remaining (for the moment) issue with Beryl. 

And FWIW, I'm running Edgy w/Beryl on a 3GHz Pentium with a Radeon
9600XT, with many Beryl extras turned on (transparent menus, wobblies,
window animations, cube lighting, etc) and it's all fast. Fast fast fast.

It's not exactly a bleeding-edge system but I have no complaints so far.


Torben

---

