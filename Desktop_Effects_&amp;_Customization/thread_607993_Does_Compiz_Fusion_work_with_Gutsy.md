---
title: "Does Compiz Fusion work with Gutsy"
date: 2007-11-09
forum: Desktop Effects &amp; Customization
---

### Post by kxr1der on 2007-11-09
I currently run Fiesty i dont currently use compiz but i would like to and i have only seen posts for compiz that tell how to make it run correctly on fiesty. I want to upgrade to Gutsy however and i want to know if it will run correctly on it. And if so how to go about installing it onto Gutsy.

---

### Post by Steveway on 2007-11-09
It comes preinstalled on Gutsy.
No really need to install anything.

---

### Post by djrobthaman on 2007-11-09
It comes with fusion already installed

---

### Post by kxr1der on 2007-11-09
Oh thats awsome, so that means i can have the cube effect on my workspaces right from installation?

---

### Post by djrobthaman on 2007-11-09
You might have to install xgl if you have an unsupported ati card.  And to get advanced settings you also need to install the config manager

---

### Post by kxr1der on 2007-11-09
ok so how do i install the config manager?

---

### Post by TadH on 2007-11-09
sudo apt-get install ccsm

---

### Post by djrobthaman on 2007-11-09
Start up synaptic (Settings>Administration>Synaptic Package Manager).
Search for compiz
Install the one that says something like compiz-config-manager

Then to run it go to Settings>Preferences>Advanced Visual Settings (or something to that effect)

---

### Post by spideygal on 2007-11-09
> **kxr1der said:**
> I currently run Fiesty i dont currently use compiz but i would like to and i have only seen posts for compiz that tell how to make it run correctly on fiesty. I want to upgrade to Gutsy however and i want to know if it will run correctly on it. And if so how to go about installing it onto Gutsy.



It does come pre-installed, however unless you have a great graphics card, I would not opt to upgrade. My memory specs are fine 1 gig and I have a 2,53 processor P4 but Gutsy had no guts on my PC. However this was due to Compiz not preforming well. I tried to get Beryl back in but was not able to so I rolled back to Feisty. 

Just a little warning but if you have the graphics card etc, go for it I would again. However I just have onboard graphics for a Dell 2400 which is not a performance winner by any means. All this said, my PC runs great on Beryl with Feisty but I even opt for Metacity as a few apps look out of place in Beryl.

---

### Post by djrobthaman on 2007-11-09
> **spideygal said:**
> It does come pre-installed, however unless you have a great graphics card, I would not opt to upgrade. My memory specs are fine 1 gig and I have a 2,53 processor P4 but Gutsy had no guts on my PC. However this was due to Compiz not preforming well. I tried to get Beryl back in but was not able to so I rolled back to Feisty. 

Just a little warning but if you have the graphics card etc, go for it I would again. However I just have onboard graphics for a Dell 2400 which is not a performance winner by any means. All this said, my PC runs great on Beryl with Feisty but I even opt for Metacity as a few apps look out of place in Beryl.

I don't know if this is the case for everybody.  I actually saw a major boost in compiz performance on my machine when I upgraded to gutsy.

---

### Post by spideygal on 2007-11-09
> **djrobthaman said:**
> I don't know if this is the case for everybody..


I agree.

 I have seen threads also stating similar effects to what I experienced.  I had Gutsy for a few weeks but I should have tried a few more options like Metacity. I did however misss my Beryl effects and just plain scrolling seemed to be a pain, I contributed this all to Compiz, not Gutsy, because wobly windows did not woble, they tried to but with Beryl, effects work perfect on my PC despite not having good graphics capabilities.

---

### Post by djrobthaman on 2007-11-09
Did you try installing the config manager? Wobbly windows are not enabled by default on gutsy and the only way to get them is to have the config manager.

Actually, the way gutsy implements compiz is a pain... Why have compiz come preinstalled but not have the thing to edit its configuration preinstalled too?

---

### Post by spideygal on 2007-11-09
> **djrobthaman said:**
> Did you try installing the config manager? Wobbly windows are not enabled by default on gutsy and the only way to get them is to have the config manager.

Actually, the way gutsy implements compiz is a pain... Why have compiz come preinstalled but not have the thing to edit its configuration preinstalled too?


Yeah I did get the compizfusion, I believe that is the name of it. The icon when loaded was invisable(did not show) but I could right click where it was loaded to and all options were there to configure.

My whole desktop affair for two weeks with Gutsy was frustrating and non responsive (slow) I chalk this up to Compiz and not Gutsy, however back on Feisty, everything is back as fast as can be, no hesitation when clicking windows.

---

### Post by kxr1der on 2007-11-10
ok i know this is off topic but i have an HP an does anybody kno if they are making attempts to fix the problems gutsy is having with HPs

---

### Post by EP3hatch03 on 2007-11-10
works perfect for me

[IMG]http://img441.imageshack.us/img441/9060/screenshot2wg8.png[/IMG]

Gutsy w/ intel GMA900 chipset

---

### Post by Rinzwind on 2007-11-10
> **spideygal said:**
> Yeah I did get the compizfusion, I believe that is the name of it. The icon when loaded was invisable(did not show) but I could right click where it was loaded to and all options were there to configure.

My whole desktop affair for two weeks with Gutsy was frustrating and non responsive (slow) I chalk this up to Compiz and not Gutsy, however back on Feisty, everything is back as fast as can be, no hesitation when clicking windows.

Regarding the icon I might know the answer:

Its 26 pixels high and the gnome panel is 1 pixel less high.
If you change your gnome panel to 26 or 27 pixels the icon will show up.

If that's the case you can edit the icon and make it 1 pixel smaller to have it show with the normanl gnome panel.

Regarding the slowdown: was that with video's? Read this and it might contain the answer:
[http://smspillaz.wordpress.com/2007/10/18/unlocking-the-full-video-potential-of-your-video-card/](http://smspillaz.wordpress.com/2007/10/18/unlocking-the-full-video-potential-of-your-video-card/)
It explains why some this are slow and how to spice it up,

Gutsy + Compiz Fusion on MY machine (Deall I9300 laptop with X300 ATI) are faster than Feisty + Beryl.

---

