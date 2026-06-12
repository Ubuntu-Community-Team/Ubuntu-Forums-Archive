---
title: "Window Frames are transparent but do not blur"
date: 2008-02-17
forum: Desktop Effects &amp; Customization
---

### Post by thomasca on 2008-02-17
Hey, I just installed the new version of Ubuntu, and all the Compiz effects work fine except the transparent windows frames don't blur stuff behind them.

---

### Post by thomasca on 2008-02-17
Sorry, let me clarify a bit.

The alpha blur doesn't work for the standard install of Compiz Fusion I have (that came with the Gutsy Gibbon install). I don't have emerald installed, I tried checking the alpha fusion box in the Compiz Fusion setting manager (in the settings for window blur) and typing in any for the window types for the alpha blur.

All the other effects work and GLX Gears work and GLXInfo says that direct rendering is working.

I'm using this on a Gateway 7210GX (same as a eMachine 2350 laptop) with a ATI Radeon Mobility U1.

If somebody could help, it would be much appreciated.

---

### Post by chavanak on 2008-02-17
Try installing emerald!!! I think then it will work

---

### Post by thomasca on 2008-02-18
> **chavanak said:**
> Try installing emerald!!! I think then it will work

Tried that, and configured it to use the alpha setting with all of the window frame. Didn't work.

---

### Post by grdnwsl on 2008-02-19
> **thomasca said:**
> Tried that, and configured it to use the alpha setting with all of the window frame. Didn't work.

I can concur with that.  I am unable to get alpha blur running on my machine.

Ubuntu Gutsy (7.10)
AMD Athlon 3500+
1GB RAM
ATI Radeon 9000 Pro

I've read in other places that you get slow performance running on slower hardware with blur enabled, however, I haven't read anything stating that the blur plugin will not load with certain hardware.

---

### Post by grdnwsl on 2008-02-20
> **grdnwsl said:**
> I can concur with that.  I am unable to get alpha blur running on my machine.

Ubuntu Gutsy (7.10)
AMD Athlon 3500+
1GB RAM
ATI Radeon 9000 Pro

I've read in other places that you get slow performance running on slower hardware with blur enabled, however, I haven't read anything stating that the blur plugin will not load with certain hardware.

So, it works fine on my home computer, which is running an nVidia 6600 card.  I'm wondering if either the ATI drivers, or the card I'm running on my other machine don't support the alpha blur.

---

### Post by mgmiller on 2008-02-22
I found the blur settings only work with emerald themes, not metacity themes as modified by compiz.

So, you need to install the emerald packages:
Do a search in Synaptic for emerald and install emerald and emeraldengine0 
or type the code:
```
sudo apt-get install emerald
sudo apt-get install emeraldengine0
```

after you have that, you can go to gnomelook.org to get an emerald theme you like and import it into the emerald theme manager.  System>Preferences>Emerald Theme Manager.

From the Themes tab click the import button and navigate to the emerald theme you want to import.

Next, change window managers so you are using Emerald.
Open the command window with Alt/F2 and type the command:
```
emerald --replace
```

Finally, follow these instructions to make sure it all works:

First turn on blur effects:
in Compiz Config Settings Manager (Advanced Desktop Effects Settings)
Turn on the "Blur Windows" effect.
In the General tab set the Blur Filter to Mipmap for maximum blur or gaussian for less blur.

Finally, enable it for emerald themes:
in emerald theme manager
go to emerald settings tab 
go to compiz decoration blur type 
select either "title bar only" to just blur behind the title bar
or "all decorations" to make everything behind the window border also blur.


Enjoy your blurry goodness.  :popcorn:

---

### Post by thomasca on 2008-02-24
Tried it. Didn't work.

I don't really know why this is.

---

### Post by brutimus on 2008-06-25
Here is what I did to blur my titlebars with metacity/compiz.

1) Go to the Blur Windows settings in the CompizConfig Settings Manager.
  - Set which windows you want this to apply to in the "Alpha blur windows" section.  I just copy/pasted all the windows from the "Focus blur windows" box.  I then disabled Focus blur and enabled Alpha blur.  Tweak other settings to your liking.

2) Run gconf-editor (either from terminal or from app launcher).
  - Navigate to /apps/gwd/blur_type and set it either "titlebar" or "all".  From what I understand, either only the titlebar will be blurred, or all the window borders.

I believe this is all I had to do.  One more setting I enabled which made my titlebars look a lot better was /apps/gwd/use_metacity_theme.  This fixed the issue I was having where when my titlebars were transparent, there was a definitely solid line where the body of the window met the titlebar. And just FYI, I'm using the Blended metacity theme and it looks very nice/smooth now with these settings.

---

