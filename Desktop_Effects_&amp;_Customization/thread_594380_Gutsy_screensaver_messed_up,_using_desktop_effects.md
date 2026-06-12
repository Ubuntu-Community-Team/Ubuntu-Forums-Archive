---
title: "Gutsy screensaver messed up, using desktop effects"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2007-10-27
A few days ago I did a fresh install of Gutsy, and I'm absolutely LOVING it except for a few minor problems.
My screensaver, which I have set to Flurry, doesn't work correctly. I'm pretty sure it's because of the desktop effects, because I had this problem before in the past while using Beryl/Compiz Fusion, but for some reason my screensaver will start but then freeze after 1 or 2 seconds. If I move the mouse it resumes like it should, but the screensaver never works. Taking into consideration the fact that desktop effects are enabled by default, shouldn't this be something that works by default as well?

Also, I have some problems playing DVDs (using VLC, I don't like Totem). VLC will start playing the DVD when I put it in, but there's usually no video (and if there is, it will die after a few seconds) but there is sound. Help?

---

### Post by 67GTA on 2007-10-28
My screensaver doesn't work in Kubuntu Gutsy without 3D effects. Something else is causing it. No one seems to have any info.

---

### Post by 67GTA on 2007-10-28
Try adding > DPMS-dependent=false to the screensaver section of ~/.kde/share/config/kdesktoprc, or Gnome equivelant. That took care of mine.

---

### Post by rainwalker on 2007-10-28
I can't seem to find the Gnome equivalent...

---

### Post by meho_r on 2007-11-05
I don't think that screensaver problem is related to Compiz Fusion. For me, in Feisty it worked perfectly with CF enabled. The problem is something in Gutsy.

BTW, when lock screen is activated in sreensaver settings, I noticed that immediately after activating screensaver something 'deactivate' it (like some fake press of a key or mouse click) and show window to enter my pass. If I press Esc, then screensaver resumes and work correctly. The question is what causes screensaver to deactivate immediately after activating?

---

### Post by tarekeldeeb on 2007-11-05
Same here ..


ONLY when i disable compiz/amerald the screensaver works fine ..
:confused::confused:

I use GNOME .. is there any solution?

---

### Post by meho_r on 2007-11-05
Well, it seems I was wrong (partially). Gutsy+CF=Screensaver problem. I updated Compiz Fusion and my screensaver works perfectly now. There were some issues with Compiz Fusion and Lock mechanism which are now corrected. Finally ;)

---

### Post by tarekeldeeb on 2007-11-05
> **meho_r said:**
> Well, it seems I was wrong (partially). Gutsy+CF=Screensaver problem. I updated Compiz Fusion and my screensaver works perfectly now. There were some issues with Compiz Fusion and Lock mechanism which are now corrected. Finally ;)

Updated ?

I already have these packages:
compiz-fusion-plugins-main (0.52)
compiz-fusion-plugins-extra(0.52)
emerald(0.3)
libemeraldengine0(0.3)

Do u have any differences ?

Thanks in advance,
Tarek

---

### Post by meho_r on 2007-11-06
compiz = 0.6.0+git20071008-ubuntu1.1
compiz-core = 0.6.0+git20071008-ubuntu1.1
compiz-gnome = 0.6.0+git20071008-ubuntu1.1
compiz-plugins = 0.6.0+git20071008-ubuntu1.1
libdecoration0 = 0.6.0+git20071008-ubuntu1.1

libcompizconfig0-backend-gconf = 0.5.2+git20071010-ubuntu1
compizconfig-settings-manager = 0.5.2+git20070912-ubuntu1
python-compizconfig = 0.5.2+git20070912-ubuntu1
libcompizconfig0 = 0.5.2+git20070919-ubuntu3
compiz-fusion-plugins-main = 0.5.2+git20070928-ubuntu2
compiz-fusion-plugins-extra = 0.5.2+git20070928-ubuntu1

You can see which were updated. Only thing I did in meantime was installation of xscreensaver, messing with it for a couple of minutes and uninstallation. When I set up gnome-screensaver again and try it - it worked. 

Hope this helps

---

### Post by tarekeldeeb on 2007-11-08
I have just as ur versions ...

i tried to remove the gnome-screensaver .. ten reinstall it .. it worked for a single session .. after I had reset the X-session .. the screensaver had the previous problem !

---

### Post by meho_r on 2007-11-09
I recently reinstalled Gutsy and I done this:

-- First I enabled Ati restricted drivers
-- Updated installed Compiz Fusion packages

(at this point screensaver still didn't work correctly)

-- I installed ccsm and made some usuall tuning
-- In console I typed: killall gnome-screensaver

After restart screensaver worked. Maybe you should try this command as it seems that it's the key. Not absolutely sure though

---

### Post by d1ss0nant on 2007-11-13
I have an identical problem - I use gnome, and when desktop effects are totally off, the screensavers work perfectly.  When Turn the effects on, I just get a black screen (when i should be seeing a screensaver).  Does anyone have any ideas?  I'm running 64 bit Gutsy Gibbon on a Compaq R3000Z with an Nvidia Geforce4 440.  Thanks

---

### Post by tarekeldeeb on 2007-11-13
i also notice that when a video is paused <but the window of the player is still opened> the screensaver works perfect, side by side with the compiz effects.

is this a clue ?

---

