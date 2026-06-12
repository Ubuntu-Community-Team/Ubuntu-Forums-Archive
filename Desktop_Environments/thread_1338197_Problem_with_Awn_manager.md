---
title: "Problem with Awn manager"
date: 2009-11-26
forum: Desktop Environments
---

### Post by amirmku on 2009-11-26
Hi everyone I am newb to ubuntu, Recenty installed AWN dock it is working but when I am shutting down, I am getting warnin mesage" **Warning! screen is'nt composited. please run compiz(-fusion) or another compositing manage**r"
I tried installing software called** Compiz fusion** from Add/remove panel but still when i am shutting down I am getting same message as stated above.
Do I need to install** advance CCSM**?.
I dont know wht to do to fix it . Please help!

---

### Post by yossell on 2009-11-26
Edit: See Shazaam's answer below for a quicker/better way

Though you may have installed compiz, you may not be running it. Normally, you can run it by going to 
system->preferences->appearance, selecting tab 'visual effects' and choosing 'extra' (also I think 'normal' is compiz too). Alternately, you can type alt+f2 and enter "compiz --replace" (w/o quotes).

Compiz comes with lots of options, lots of eye candy and some useful functionality. It also requires, I think, 3-d acceleration, and not everybody can get it running smoothly on all hardware. It allows various transparent, glassy effects, which (I'm guessing) is probably what Awn wants. 

Two points: (a) compiz may be overkill for this. It may be simpler  getting xcompmgr and running that. (b) it may not really matter that much for Awn, despite its warning messages. If you're happy with how Awn is working, and you think it looks fine, then I don't know if these warning messages are anything to worry about. In my limited experience of cairo-dock and cairo-clock, they too complain that they want compositing managers but, despite some big black borders, they seem to run functionally without one.

yossell

---

### Post by Shazaam on 2009-11-26
Gui way to run AWN without Compiz...
1. Go to Applications>System Tools>Configuration Editor.
2. Go to apps>metacity>general.
3. Checkmark "compositing_manager".

Or...
Enter this in terminal to get to the same place-
```
gconf-editor
```

---

### Post by yossell on 2009-11-26
just a ps

I hadn't tried metacity as a compositing manager before. It works fine, but when I later tried to change appearances and re-enable some fancy compiz effects, my told me it was unable to do this and started behaving very strangely. Simply going back and unticking the box brought everything back to normal - and appearance could be changed as usual.

It may be a quirk of my system, but I thought I'd just mention it in case the same happened to you.

---

### Post by Ginsu543 on 2009-11-27
I personally use Fusion Icon to change Compiz/Metacity settings. You can find it in Synaptic by searching for "Compiz." You can then add it to System --> Preferences --> Startup Applications so that it will load every time you boot:
1) Click "Add"
2) Name it something like "Compiz-Fusion Icon"
3) Add "fusion-icon --no-start" to the command line (without quotes)
4) Add comment if you'd like
5) Click "Save"
When you reboot, you will get a blue icon in the notification area. Just right-click it and it will give you options to choose whether you want to use Compiz or Metacity as your compositor.

---

