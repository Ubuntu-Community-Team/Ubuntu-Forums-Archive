---
title: "Guild Wars and Linux"
date: 2007-04-20
forum: Gaming &amp; Leisure
---

### Post by Nigters on 2007-04-20
Hello people.

I'm considering switching to linux instead of windows because err well i just want to try something else.

Now i havent even installed it yet, only tried a live-cd and it seemed quite nice, now questions.

Im playing Guild Wars and Battlefield 2, i got a guide for making BF2 work but a GW is not so near, [http://ubuntuforums.org/showthread.php?t=283122](http://ubuntuforums.org/showthread.php?t=283122)         at that page there is some sort of a guide, but it seems to me that the steps done there is no longer neccesary to make GW run, because of some sort of Xcursor Wine update etc. is that true? or should i still follow the steps in the guide? if i should still follow the guide how do i run one of those scripts, in the automated install code box? and the file to DL at the bottom of the page does that contain Wine already? or do i have to go to the wine page and download and install the newest version myself?

And in general will most games be able to run with a minimum of configuration on Wine?

Also is it worth paying for Cedega to be sure the games will run?

Thank you for your help, hope it was readable :)

---

### Post by AndrewRiedi on 2007-04-20
Cedega is generally not worth paying for because Wine has more advanced D3D support now, and is improving quite nicely.  I am working on the Wine cursor issues (which should be fixed for GW now).  We have someone working on sound issues also, and we will have someone start implementing D3D10 in the summer.  There is still an issue with lighting in GW if I remember correctly, but there is a workaround for that I believe.  Check appdb.winehq.org for information on specific applications and games.  Games that require copy protection usually will not run in wine right now.  That will probably be fixed at some point in the future, but that could be a very long time.  (eg. over a year)  If you have any more specific questions, just ask.

[Battlefield 2]("http://appdb.winehq.org/appview.php?iVersionId=3438")
[Guild Wars]("http://appdb.winehq.org/appview.php?iVersionId=7530")

PS: Even though the Guild Wars entry says the cursor doesn't work with Wine 0.9.35, it does.  I spoke to the Ubuntu Wine package maintainer and he fixed everything up for that.

EDIT: Fixed links.

---

### Post by Nigters on 2007-04-21
Hi and Thank you for the help

It seems the links you posted dont work... maybe jsut a server issue so ill wait...Edit: The links were corrupted... double html in the front :/ edited myself and is able to enter the sites now :)

So to run GW should i follow the steps in the guide you linked too? or will it just not work right now, or will it just work when i install it?

and should i before anything simply install plain Wine?

---

### Post by AndrewRiedi on 2007-04-21
1) Go [here]("http://winehq.org/site/download-deb") for instructions on getting the latest Wine installed.
2) Open a terminal and use Wine to install GW.  (eg. wine "d:\name_of_installer.exe")
3) Do the tweaks that they recommend on the appdb.
4) Run the game.

---

### Post by Nigters on 2007-04-21
> **AndrewRiedi said:**
> 1) Go [here]("http://winehq.org/site/download-deb") for instructions on getting the latest Wine installed.
2) Open a terminal and use Wine to install GW.  (eg. wine "d:\name_of_installer.exe")
3) Do the tweaks that they recommend on the appdb.
4) Run the game.

Ty very much, now for a general question :)   i saw a vid of a linux OS having the same look as the Windows Vista Aero theme... where can i get that? and i also saw that some kind of "bubbles" were following the trail of the mouse pointer, where can i do that too?

Best Regards... me.

---

### Post by AndrewRiedi on 2007-04-21
A little history:

A while back David Reveman released something called Compiz.  Then some people started adding all sorts of effects to it and calling it Compiz-Quinn.  (Quinn is the person that was leading the extra features.)  This new group of people believed that they had something different in mind than the original Compiz project and forked it to create Beryl.  What you saw is Beryl using Emerald and a Vista theme.  Since then, the Compiz people and the Beryl people have decided they want to merge back together again since their views are not all that different.  They are now working on merging the projects back together, so it will be a while before another release hits.  Anyhow, that should answer your question.  :)

---

### Post by Nigters on 2007-04-21
Thank you quite so much, looking on their page now... makes my eyes bleed over the joy Vista users are missing !

---

### Post by AndrewRiedi on 2007-04-21
> **Nigters said:**
> Thank you quite so much, looking on their page now... makes my eyes bleed over the joy Vista users are missing !

:)

---

