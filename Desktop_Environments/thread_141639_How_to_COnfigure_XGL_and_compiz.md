---
title: "How to COnfigure XGL and compiz??"
date: 2006-03-08
forum: Desktop Environments
---

### Post by profediego on 2006-03-08
Hi i install those things, an i love them.  The thing is i feel i dont have all the options i should have, i mean, i have no translucency effect on windows, i want that.  Could somebody tell me how to get it, and please whats the configuration on the keyboard to use every aspect of xgl and compiz, i have managed to discover several o f them but not all.

Or even better, id there an app or a CLI command or and .txt file or something that let me configure the xgl and compiz.

Thanks ppl

---

### Post by andrewsawyer on 2006-03-08
from terminal type 'gconf-editor' minus the quotes.

then choose:

Apps >> Compiz >> Plugins

From there you can drill down on each of the plugins that you have installed (or loaded - not sure which), and you can see what key combination does what.  Button 3 and 4 are related to up and down scroll on your mouse.

To check what plugins you have installed, use the same prog and go to:

Apps >> Compiz >> General >> Allscreens >> Options

And check under the active_plugins list.  You should have (in this order);

gconf
decoration
wobbly
fade
minimize
move
placce
resize
scale
switcher
cube
rotate
zoom

I think Skydome is part of the cube plugin and doesn't need anything extra, but I've not got it working yet myself.

I have also had a problem getting the Super Key (Windows Key) working with Compiz, so I couldn't get the zoom function to work.  To fix this I swapped <Super> for <Alt><Shift>.

I hope this helps.

---

### Post by ronmarley1 on 2006-03-08
Hi profediego,
Not sure if it helps (you may already be past this), but here's a how-to on the new eye candy.  I can wait!
[http://www.ubuntuforums.org/showthread.php?t=131253](http://www.ubuntuforums.org/showthread.php?t=131253)

---

### Post by profediego on 2006-03-12
to Andrewsawyer, man thank you a lot, now i can control my desktop much better, thanks a lot.

Only thing left to activate is translucency effect, and a effect where all opened windows kind off acomodate in the desktop area, i dont know how to do that.

To ronmarley, thank too, but i dont think that info is for me i have an nvidia card  and i am usin breezy not dapper, but hey thanks for answer.

---

### Post by MetalMusicAddict on 2006-03-12
Check [THIS]("http://www.ubuntuforums.org/showthread.php?t=140687") little app being developed right here.

---

### Post by profediego on 2006-03-12
I already know how to 'Scale' \\:D/  he he he it was F12... only thing left is translucency effect.

If someone out there could help, please i will apreciate.

---

### Post by andrewsawyer on 2006-03-12
You should have translucency in the title bars as standard all the time.  To make whole programs translucent, you should be able to use Ctrl + Shift + up/down scroll button on mouse.

---

### Post by profediego on 2006-03-13
Man, Andrew,  awesome, i just saw your desktop video, i am shakin i want something like that on my PC, what are yyour pc specs if i could know please.  
Let me tell you that <control><shift> mouse button 3 or 4, doesnt seem to work to do the translucency effect on my desktop, dont know what could be, i search all over compiz config editor i dont see any key combibnation like that, maybe is someqhere else i dont know.

One more question, how do i get the water effect on my desktop? are there more effects like that? 

Thanks a lot.:mrgreen:

---

### Post by andrewsawyer on 2006-03-14
Hiya,

Glad to hear you liked my vid.  I've actually been amazed how many people have been downloading it - my server is getting about 1Gb bandwidth per day just for that (plus whatever goes through the mirrors).

My pc is an Athlon 3800+ 64bit dual core, 2Gb ram, 250Gb sata2 HDD, nVidia 6600GT graphics card, setup with TwinView.  I'm running 64 bit Dapper.

The water effect it a program that you can get via apt-get/synaptic called xdesktopwaves.  There is a how-to in the Breezy tips and tricks by Poofy on how to set it up.  One thing to note though is that the water effect is quite CPU intensive - it doesn't use the GPU, and has nothing to do with Xgl.

loading up gconf-editor, and drilling down on Apps >> Compiz >> Plugins >> Opacity >> Screen0 >> Options should tell you the key combo to get transparency working.  It it is not there, then you probably don't have the pluging loaded.  You need to set it to load as per my first post on this thread.

Best of luck!

---

### Post by jasay on 2006-03-14
Full window opacity wasn't originally included in compiz, so if you have an old version (like the one in the dapper repos) it won't have the plugin to load.  You'll have to either [get the plugin]("http://www.ubuntuforums.org/showthread.php?t=132063&highlight=true+opacity") and install it manually or get a [newer version of compiz]("http://www.ubuntuforums.org/showthread.php?t=139265") like this one made by DeeZiD from cvs that alos include skydome.

---

### Post by profediego on 2006-03-15
Thanks ppl for all the help, now i have my desktop as i want it to and prepare to show my friends and maybe get a few to switch he he he :mrgreen: 

Thanks Jasay for the opacity configuration and thanks Andrew for your friendly attitude.

---

