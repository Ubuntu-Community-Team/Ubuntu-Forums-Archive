---
title: "Desktop effects problems with nvidia mx400"
date: 2007-09-06
forum: Desktop Effects &amp; Customization
---

### Post by andymushu on 2007-09-06
I know there are a lot of threads about this, but i looked through a lot of them and i didn't see what i needed. if there is a thread that answers my question please post the link. I just spent 3 hours getting the restricted drivers for my nvidia geforce 2 mx400 pci ideo card to work, all for these desktop effects. I have used them on another computer and i just loved them. So i tried to enable desktop effects and it says "unable to enable desktop effects". Does anyone have any ideas?

Any help would be extremely appreciated.

-just in case you need to know, this is what my lspci says about my video card:
01:06.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

---

### Post by smartboyathome on 2007-09-06
Try doing a compiz --replace in a terminal and post what you get here.

---

### Post by allwin on 2007-09-06
You need to get the nvidia drivers by downloading ENVY.  I have the same card and eventually got Beryl running (haven't tried Compiz Fusion out just yet in that environment).  Need to manually edit xorg.conf as well.  The 9xxx driver is the one you want, and Envy will figure that out for you.  Then you just follow one of the Beryl install threads for nvidia.

The only remaining problem I have is the famous nvidia BLACK WINDOW bug occasionally.  Nothing you can do about that but fiddle with the settings until you get it to minimally occur.

The "desktop effects" built in didn't work worth a @#$% for me when I installed Feisty (clean) on my experimental machine, a 2002 model Pentium III Dell.  But after installing Beryl 0.3.0 and Emerald, it worked just fine after tweaking.

Hope this helps.  Have at it.

---

### Post by andymushu on 2007-09-06
thanks for the help. i actually have envy downloaded and i think i used it to get the drivers... lol, i did so much to try to get it to work, im not even sure what i did. now my screen resolution is set at 800x600, even though i have it configured in the xorg.conf and it used to have it in the screen resolution menu, but now its just 800x600. any ideas? 

btw, here is what i get when i do compiz --replace. 

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

doesn't seem like very good news...

---

### Post by Inxsible on 2007-09-07
are you trying to setup compiz(aka desktop-effects) or compiz-fusion ?

there is a difference between the compiz - that comes pre-installed with Feisty and compiz-fusion -which is a merger between compiz and beryl

---

### Post by andymushu on 2007-09-07
at first i just wanted the desktop effects, but now i kinda want compiz fusion too. update: somehow i got the desktop effects to work (kinda). when i enable them everything is really laggy and a lot of windows don't act right (some will be white, one window will always be on top, etc). i was also missing the minimize, maximize, and close buttons on every window. then i tried to run beryl just to see if it would work. it did, in a sense. much of the same that desktop effects did. i have a feeling i may be trying to squeeze too much out of this card, but i have heard of beryl and compiz running on much older cards, so you never know. again, any help with this would be much appreciated.

---

### Post by andymushu on 2007-09-07
bump

---

### Post by bachi.bazofia on 2007-09-07
I have the same graphic card, and it's runing Beryl, not Compiz Fusion. I have that problem at the begining. Try to refresh the skin window theme. It works for me in Beryl...

---

### Post by andymushu on 2007-09-08
alright, i got compiz fusion working pretty good. the fire animations are pretty choppy, but i assume thats just my video card. when i try to do control+alt+left or right or the mouse, it flips the screen, but it isn't a cube. it is just a two sided sheet of paper type of deal. can anyone tell me how to fix this please?

---

### Post by andymushu on 2007-09-08
bump

---

### Post by Inxsible on 2007-09-08
Go to System-->Preferences-->CCSM. Click on General Options. Then select Desktop Size and make sure you have these settings```
Horizontal Virtual Size = 4
Vertical Virtual Size = 1
Number of Desktops = 1
```

---

### Post by andymushu on 2007-09-08
thank you so much. working perfectly now. i have seen a plugin to make the windows come off of the cube in a 3d view. how do i enable that?

---

### Post by andymushu on 2007-09-08
bump

---

### Post by Inxsible on 2007-09-08
> **andymushu said:**
> bumpenable the 3D Windows plugin. and give it a little time before bumping your threads over and over.

---

### Post by andymushu on 2007-09-09
ok i downloaded the compiz-fusion unsupported and unofficial plugins, which gave me the options for 3d windows and cube atlantis. but when i enable them, compiz just breaks and it doesn't start back up. it seems like i am missing a dependency or something, but i can't figure it out. sorry for the bumping, i am kind of impatient. but thank you so much for your advice, it really helped me with this whole project.

---

### Post by andymushu on 2007-09-10
bump

---

### Post by darkazurka on 2008-05-30
(I also have nvidia mx400)
> **andymushu said:**
> I was also missing the minimize, maximize, and close buttons on every window.

It's called the **Window Decoration Plugin** in Compiz configuration settings manager.
I have problems with this plugin on Hardy. Whether I turn it on *or* off nothing happens. Window decoration doesn't show up, and it has been gone for a very long time. (since when I started using Gutsy, and after some bad time in Gutsy it stopped showing the window decoration when compiz was enabled)

---

