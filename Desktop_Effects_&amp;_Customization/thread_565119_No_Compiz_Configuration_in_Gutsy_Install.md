---
title: "No Compiz Configuration in Gutsy Install"
date: 2007-10-01
forum: Desktop Effects &amp; Customization
---

### Post by Posterus on 2007-10-01
i recently installed the Gutsy Beta on my desktop and compiz only runs if i compiz --replace in terminal...but once i exit the terminal compiz stops and there is no compiz configuration under System -> Preferences.  Any advice is much appreciated

-Posterus

---

### Post by overlord.gaurav on 2007-10-01
People are having a lot of Compiz issues in Gutsy Gibbon. Since, Gutsy Gibbon is unstable, it is hard to seek support for it now.

---

### Post by Perpetual on 2007-10-01
I think since compiz-fusion is also in it's youth and working out bugs, it's safe to say a lot of the issues are not Ubuntu related but CF related as I have seen breakage under other distributions as well.

Compiz forums are flooded with threads regarding trouble with latest updates... [http://forum.compiz-fusion.org/forumdisplay.php?f=86](http://forum.compiz-fusion.org/forumdisplay.php?f=86)

---

### Post by Posterus on 2007-10-01
o0o ic, well thanks for letting me know hah

---

### Post by Faud on 2007-10-01
You can download the compiz settings manager, Im at work but give me a few and let me see if I can find it. Im thinking it is in the repositrys though

---

### Post by Faud on 2007-10-01
> **Posterus said:**
> i recently installed the Gutsy Beta on my desktop and compiz only runs if i compiz --replace in terminal...but once i exit the terminal compiz stops and there is no compiz configuration under System -> Preferences.  Any advice is much appreciated

-Posterus

Also, just to make sure, you did turn desktop effects on right ? It doesnt say compiz, it just says desktop effects

---

### Post by tact on 2007-10-01
As a work around instead of running compiz --replace in terminal....  press ALT-F2 and type compiz --replace  in the dialog box that pops up.   This will keep compiz running without a terminal window hanging around until your next reboot

You can also create an entry in system>preferences>sessions for compiz --replace to have it run at every start up.  (Be careful tho as some systems seem to need a delay between normal desktop starting and compiz starting - in this case the sessions entry should point to a little script you create that causes a 10 second sleep before compiz starts)

For what its worth - I had to do the above (script with 10 second delay before starting compiz) when I was running Feisty.   

After installing the Gutsy beta I find I can turn that all off (disable in sessions) as gutsy automatically starts compiz for me.  (i.e. when I had "compiz --replace" in sessions I was actually restarting compiz a second time un-necessarily).

---

### Post by Posterus on 2007-10-01
> **Faud said:**
> Also, just to make sure, you did turn desktop effects on right ? It doesnt say compiz, it just says desktop effects

um...there is no desktop effects in my Gutsy install, my guess is since compiz is pre-installed it doesnt need the desktop effects

-Posterus

---

### Post by tact on 2007-10-01
...oh ya!   There IS limited configuration in Gutsy for compiz.

Go to System>Preferences>Appearance   click on the "Visual effects" tab.

Maybe this is why you have to manually start compiz - its possibly turned off there.   If so - turn on Visual effects and forget about all the workarounds in my previous post.

---

### Post by Posterus on 2007-10-01
Faud, thanks that would be great if you could find that


-Posterus

---

### Post by tact on 2007-10-01
> **Posterus said:**
> Faud, thanks that would be great if you could find that


-Posterus

Stop looking "Desktop Effects" is not a part of Gutsy beta.

Look where I said in System>Pref>Appearance
select the visual effects tab
enable to some level you prefer (there are only 3(?) choices)

---

### Post by Posterus on 2007-10-01
> **tact said:**
> Stop looking "Desktop Effects" is not a part of Gutsy beta.

Look where I said in System>Pref>Appearance
select the visual effects tab
enable to some level you prefer (there are only 3(?) choices)

yes but in the manual install of compiz there is a manager so there should be a manager for it in Gutsy.

---

### Post by Faud on 2007-10-01
compizconfig-settings-manager 

This can be found in your pakage manager.
Just mark for install, this will put a settings manager on in your systems--> preference.

In Gusty you shouldnt have to hit AltF2 or run compiz from a terminal (to my knowdledge) because once you turn on the visual effects it loads compiz up and keeps it running

---

### Post by Faud on 2007-10-01
> **tact said:**
> Stop looking "Desktop Effects" is not a part of Gutsy beta.

Look where I said in System>Pref>Appearance
select the visual effects tab
enable to some level you prefer (there are only 3(?) choices)


Tact, thanks for the correction on the actual name. That was a bad memory recall from work...my apologies

---

### Post by LESLIEx317537 on 2007-10-02
Yea, I had no advanced desktop settings after a fresh install from the CD.

I updated everything, rebooted, enabled the advanced video drivers then in the Synaptic Package Manager, I added compizconfig-settings-manager as Faud said.

I now have all the advance settings under System -> Preferences -> Advanced Desktop Effects Settings.

---

### Post by Drakkor on 2007-10-09
I get all the settings in System>Preferences>Appearance.>.Visual Effects tab>Custom>
Preferences to get to the CompizConfig,lol :)

---

### Post by Posterus on 2007-10-09
> **Drakkor said:**
> I get all the settings in System>Preferences>Appearance.>.Visual Effects tab>Custom>
Preferences to get to the CompizConfig,lol :)

Drakkor, is there anything you had to do to get that? because on my visual effects tab there is no "Preferences" button.  Could just be due to the fact that i havnt installed the compiz manager yet..thanks to Faud btw:)

---

### Post by Drakkor on 2007-10-09
Yeah, I would probably install the compiz manager, are you using Gutsy, you still have 
Fiesty Fawn user,lol :) CompizFusion rocks !

---

