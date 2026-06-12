---
title: "how do i use Emerald themes."
date: 2007-07-03
forum: Desktop Effects &amp; Customization
---

### Post by fongs on 2007-07-03
Hi i have installed emerald themes and don't know how to use it . Please help

---

### Post by Vajra Vrtti on 2007-07-03
*System -> Preferences -> Emerald Theme Manager*.
(also accessible right clicking the Beryl tray icon)
Just select the theme you want to use.

---

### Post by Adler on 2007-07-03
fongs,

Whare are you running? Beryl or CompizFusion? And, what repositories have you used for the install? Beryl / Compiz have combined, and will be called Fusion.

Many of use have tried Emerald Thmes with Fusion with little or no success. 

Adler

---

### Post by NeoLithium on 2007-07-03
I have Fusion running with Emerald and no problems.  :)

---

### Post by Adler on 2007-07-03
NeoLithium,

OK, care to share? LOL!

I've done Beryl from SVN, ran great. Do Fusion from repositories, runs great, but those Emerald themes seem to be missing. Ya' gotta love that 3-D Cube, plus all the new stuff that Fusion has.

Also, I managed (with the help of the Forum here) to get that pathetic Radeon XPress 200M card to go 3-D and Beryl. Now I'm with NVIDIA. 

Any help would be appreciated and a "Sticky".

Adler

---

### Post by fongs on 2007-07-03
Ok seem to have found it by right clicking beryl icon / select window decorator (emerald)
 Then system / preferences / Emerald theme manager choose theme and it works. It seems it was not on by default.

Just anther thing how do you theme all buttons and icons and is there another type of dock besides kiba as it was to slow and buggy.

---

### Post by Vajra Vrtti on 2007-07-03
*System -> Preferences -> Theme*
Press the *Customize* button and select the *Icons* tab.
Chose an available icon set or install a new one.
The icons will be used in Beryl even if not using the Metacity theme.

---

### Post by NeoLithium on 2007-07-03
> **Adler said:**
> NeoLithium,

OK, care to share? LOL!

I've done Beryl from SVN, ran great. Do Fusion from repositories, runs great, but those Emerald themes seem to be missing. Ya' gotta love that 3-D Cube, plus all the new stuff that Fusion has.

Also, I managed (with the help of the Forum here) to get that pathetic Radeon XPress 200M card to go 3-D and Beryl. Now I'm with NVIDIA. 

Any help would be appreciated and a "Sticky".

Adler

I dunno, a few people seem to have tons of problems and some with none at all!  With Feisty, I used the Tuxfamily repositories, and it all worked out fine; with gutsy I just use the standard repos and have no problems.  I just run it all with compiz --replace -c emerald and BING.  Happy fusion and nice emerald themes.  Could be that a few of us just got really lucky though.

EDIT - The initial guide I used, was here: [http://ubuntuforums.org/showthread.php?t=481314&highlight=Compiz+Fusion](http://ubuntuforums.org/showthread.php?t=481314&highlight=Compiz+Fusion)  has all the info that you need for the Tuxfamily repositories if you don't have them yet.

---

### Post by Adler on 2007-07-03
> Could be that a few of us just got really lucky though.

NeoLithium,

@ this point I would have to say - yes. You did get lucky. Do you have any Screenshots to prove your point?

I've seen things like this happen before, tried to do it again, then failed. If, you know what I mean.

I'm sure that others will join in here. 

Adler @ 109 degrees / 43 celsius @ 8 PM.

---

### Post by NeoLithium on 2007-07-03
[http://members.shaw.ca/jbeerwart/Screenshot.png](http://members.shaw.ca/jbeerwart/Screenshot.png)

Desktop screenshot? Well, average one, but nothing fancy unless you want to see my synaptic with the fusion packages installed. LOL  Just a quick one I did for a discussion on IRC; though it doesn't look too different from my last beryl install.  Haven't done much fancy stuff lately though.

---

### Post by Adler on 2007-07-03
NeoLithium,

Perhaps we have misunderstood each other. I can post screen shots all day long --

[[IMG]http://img228.imageshack.us/img228/3200/snapshot11ly4.th.png[/IMG]](http://img228.imageshack.us/my.php?image=snapshot11ly4.png)

Plus, do YouTube posts recording my Desktop in action. 

I just want those Emerald Themes back versus the basic Fusion WM.

Adler

---

### Post by whereareyoutakingme on 2007-07-06
i installed beryl manager from a terminal window, then installed emerald also from a terminal (apparently i didn't already have it).  then i changed my windows decorator to emerald and opened the emerald theme manager from the red diamond.  i doubled clicked on the 45402-scaled_black_mod theme (after having changed the extension to .emerald) at which point i got the following error message:

(emerald:19832): Gdk-CRITICAL **: gdk_drawable_unref: assertion `GDK_IS_DRAWABLE (drawable)' failed


can anyone tell me what i have done wrong??

---

### Post by avik on 2007-07-06
I used [this guide]("http://ubuntuforums.org/showthread.php?t=485284"), and Emerald worked for me from the beginning.  Weird...

---

### Post by Adler on 2007-07-06
avik,

I'll have to try what you just posted.

There seems to be some confusion here between the good old days of getting Beryl running, and the new Compiz-Fusion.

Do you have the new sources / repositories that work? Can you reference a "How To"?

BTW, I've just gone 7.04 64-Bit, and like to see success here with Fusion.

Adler

---

### Post by avik on 2007-07-06
> **Adler said:**
> avik,

I'll have to try what you just posted.

There seems to be some confusion here between the good old days of getting Beryl running, and the new Compiz-Fusion.

Do you have the new sources / repositories that work? Can you reference a "How To"?

BTW, I've just gone 7.04 64-Bit, and like to see success here with Fusion.

Adler

I did reference a HOWTO.  I'm also running 64-bit, so I know as a fact it works.  The HOWTO I linked to (which I didn't write) actually talks about a script that compiles Compiz-Fusion from source, so it works with amd64.

Again, it's [http://ubuntuforums.org/showthread.php?t=485284]("http://ubuntuforums.org/showthread.php?t=485284").

---

### Post by deGz0rx on 2007-07-07
hmm
I installed beryl 2 days ago from synaptic package manager, configured it to my needs (lol) and it works fine.
now i installed emerald using terminal, and i can start it from 
system > preferences > emerald theme manager
and window shows up but when i select a theme nothing happens.
when i right click on beryl on top panel i see emerald right under "beryl settings manager" but again, it doesnt work.
when i open "select window manager" tab, i dont see emerald, there are just beryl, compiz and metacity.

damn, i`m so stupid :cry:
pls help

edit: i use ubuntu 7.04 Feisty Fawn

---

### Post by sbartz on 2007-07-12
It's under window decoraters. You may need to restart.

---

### Post by maestrobwh1 on 2007-07-13
I upgraded a feisty distro to gutsy today.... and now I can't reinstall emerald for beryl/compiz fusion.  

The only theme managers I have are aquamarine, kde and gtk.  They are kind of short on flair to say the least, and none of them really allow for adding themes easily.   KDE themes usually have to be downloaded from kde-look as source and usually fails.

Is there a theme manager for compiz specifically?

When I go to adept, and select install for emerald, nothing happens... I don't even get a "break."  I tried aptitude, and it uninstalled three seemingly unrelated packages.

Oh, and compiz fusion puts a rather "in-the-way" border around things.  How do I get rid of this, if anyone knows.

---

