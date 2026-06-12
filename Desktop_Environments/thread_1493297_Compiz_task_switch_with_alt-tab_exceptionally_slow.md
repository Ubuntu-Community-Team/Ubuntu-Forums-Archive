---
title: "Compiz task switch with alt-tab exceptionally slow"
date: 2010-05-25
forum: Desktop Environments
---

### Post by jerwilkins on 2010-05-25
Quite recently, after upgrading my desktop to Lucid--but not immediately after--my alt-tab task switcher began to act up.
The alt-tab action takes nearly an entire second to switch between windows (Meaning, each <tab> while I'm holding <alt> takes approximately 1s. Quite unworkable.). This happens even with the static application switcher.

I am using Compiz. My laptop doesn't suffer from this issue, but is also running a fully updated Lucid install. I have cross-checked Compiz settings between the machines and they are identical. 

The effects themselves seem quite smooth (i.e., doesn't appear to be a graphics acceleration bug), but the delay is unmanageable. I've seen that other posters have had similar issues, but I cannot seem to find a relevant solution.

Any help is greatly appreciated.

---

### Post by Jart44 on 2010-05-25
Jer,
Is your ALT+TAB switcher been defaulted at an earlier time? In Window Management what switcher is enabled in your Compiz? Using Ubuntu Lucid-Compiz my ring switcher is activated using <SUPER>+<TAB> not <ALT>+<TAB>for switching desktops. I have Disabled all other switchers for simplicity. So Static Application Switcher and Shift Switcher are UNchecked, but if you want to use them there are options for speed in Misc settings.If you go to: CCSM>Ring Switcher>Misc.Options> you will see speed and timestep. In speed I've set 1.138, in timestep I use the same number. It's fast and functional. Hope I have not misinterpreted your question.
Good Luck

---

### Post by jerwilkins on 2010-06-08
Jart, thanks for the response!
Sorry took so long to follow up, but I don't believe I got an email notification.

I have no other task switcher enabled. 
Additionally, I've tried the timing values you suggested in the Static Application Switcher--no luck.

Thanks in advance for any further aid!

---

### Post by stoanhart on 2010-06-16
I am having the same issue, and find it is only occurring when I have several PDFs open (in my case, using Okular). Specifically, the PDFs are full scans of textbooks (ie: 900+ JPEGs bundled together), though some of the PDFs are school assignments, and thus 1-2 page text-based PDFs. 

If I had to guess, all these bitmaps are being cached in memory by X (my Xorg process is using > 500MB of RAM right now), causing some less-used bitmaps such as the window screenshots used by the window switcher to be swapped out. The frustrating thing is I have lots of free RAM, so this swapping is unnecessary.

---

### Post by jerwilkins on 2010-06-29
In my case, it is slow regardless of open processes (straight from boot, even if I just open gEdit or terminals).

---

### Post by juliobahar on 2010-07-09
I have the same issue just after a recent upgrade (using upgrade manager) my graphics seems to be unbearably. To the extent that I've reverted back to Metacity after being using Compiz for quite sometime. 

I tried the new kernel 2.6.34 (mainline) it didn't help.

I have an Intel 8xx graphic card, on a toshiba Satellite A55. Ubuntu is becoming less friendly by the day, I have problems with two out of three of my laptops all occurring after Lucid install.

I don't know it might be me!!!

---

### Post by ldrn on 2010-08-02
I ran into a similar issue -- well, it sounds identical, except I'm on Karmic with the machine in question. I was able to fix it by running ccsm, going into Static Application Switcher, and changing "Speed" to 25 under "Behavior" -- and more importantly, setting Saturation, Brightness, and Opacity to 100 under Appearance; lightning fast again.

After fiddling with the settings very briefly, though, Opacity is instant, Brightness is very quick, but Saturation was what made it incredibly slow for me. It might just be my graphics card, which would fit, since it is a Poulsbo -- but just in case, this might help others. :)

---

### Post by jerwilkins on 2010-08-03
This worked flawlessly!
ldrn, you are outstanding :)

> **ldrn said:**
> I ran into a similar issue -- well, it sounds identical, except I'm on Karmic with the machine in question. I was able to fix it by running ccsm, going into Static Application Switcher, and changing "Speed" to 25 under "Behavior" -- and more importantly, setting Saturation, Brightness, and Opacity to 100 under Appearance; lightning fast again.

After fiddling with the settings very briefly, though, Opacity is instant, Brightness is very quick, but Saturation was what made it incredibly slow for me. It might just be my graphics card, which would fit, since it is a Poulsbo -- but just in case, this might help others. :)

---

### Post by svenni on 2010-09-14
Also note that under Static Application Switcher, there is a tab named Behaviour. Under this, there is a slide named Popup Window Delay. Setting this to 0.08 makes the popup window show much snappier, and still keep it from showing when fast-clicking Alt+Tab. The default of 0.2 gives me a feeling of lag everytime i hit Alt+Tab to see the open windows.

As well, if you have enabled Alpha Blur under the Blur Windows settings and you are using Opacity of less than 100 in Static Application Switcher, you might want to disable Blur Occulsion. This will avoid blurring several windows on top of each other, and instead blur only the top one.

---

