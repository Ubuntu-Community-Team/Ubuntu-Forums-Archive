---
title: "Open Sonic"
date: 2010-06-22
forum: Gaming &amp; Leisure
---

### Post by metalf8801 on 2010-06-22
Has anyone else played Open Sonic? 

If you have you most likely notice the sound doesn't work out of the box on Linux. The suggestion on the official website to uninstall pulseaudio caused problems for me. For example I lost my volume control icon on the Indicator Applet and other sounds stopped working. Luckily there were some other suggestion the one I liked the best was posted [http://opensnc.sourceforge.net/forum/viewtopic.php?id=100](http://opensnc.sourceforge.net/forum/viewtopic.php?id=100) 

at the end is says to use the command 
aoss opensonic_launcher
which didn't work for me instead go to 
System > Preferences > Main Menu > games > Open Sonic 
from 
Command: /usr/games/opensonic
to 
Command: aoss /usr/games/opensonic

If you haven't played the game before see links 


Homepage 
[http://opensnc.sourceforge.net/home/index.php](http://opensnc.sourceforge.net/home/index.php)

There are a few ways to install it 
from launchpad [https://launchpad.net/~szymonw/+archive/ppa](https://launchpad.net/~szymonw/+archive/ppa)

from the PlayDeb repository so you would have to do this [http://www.playdeb.net/updates/ubuntu/10.04/#how_to_install](http://www.playdeb.net/updates/ubuntu/10.04/#how_to_install) 
and then you could add the game from here
[http://www.playdeb.net/software/Open%20Sonic](http://www.playdeb.net/software/Open%20Sonic)

its also in djl which is where I found it to begin with but djl isn't as easy to install as PlayDeb 
[http://en.djl-linux.org/](http://en.djl-linux.org/)

Have fun playing 
Dan

---

### Post by donkyhotay on 2010-06-23
I played it a bit, it was pretty fun however the sound issues were annoying. I was able to fix them following the instructions on the opensonic site however they came back after updating a few weeks later. I uninstalled because the game wasn't worth the hassle.

---

### Post by metalf8801 on 2010-06-23
> **donkyhotay said:**
> I played it a bit, it was pretty fun however the sound issues were annoying. I was able to fix them following the instructions on the opensonic site however they came back after updating a few weeks later. I uninstalled because the game wasn't worth the hassle.

What did you do to fix the sounds did you uninstall pulseaudio or did you do the other option? Also what happened after the updates? 

Thanks
Dan

---

### Post by donkyhotay on 2010-06-23
> **metalf8801 said:**
> What did you do to fix the sounds did you uninstall pulseaudio or did you do the other option? Also what happened after the updates? 

Thanks
Dan

Can't remember exactly (it was some time ago). I know I didn't mess with pulseaudio, I did something with opensonic itself and I know I found the instructions on their page somewhere. After automatic update from playdeb my changes needed to be reimplemented and it wasn't worth looking up and doing it again so I uninstalled.

---

### Post by junebugg on 2010-06-24
This looks like it would be pretty fun. I'll have to try it sometime. I just wonder what Sega would have to say about it... Hopefully they can keep working on it. Thanks for sharing!

---

### Post by donkyhotay on 2010-06-24
> **junebugg said:**
> This looks like it would be pretty fun. I'll have to try it sometime. I just wonder what Sega would have to say about it... Hopefully they can keep working on it. Thanks for sharing!

I've heard (though nothing official) that they are planning on creating their own art/graphics to make it a completely FOSS game, but of course with the ability for people to import their own to play original sonic, similar to what armagetronad does. By default armagetronad looks nothing like the movie tron but there are moviepacks you can install that change the graphics and sound effects to match the original movie. This is of course highly questionable as to legality and copyrights but thats why armagetronad doesn't support/host those moviepacks themselves.

---

### Post by metalf8801 on 2010-06-25
> **donkyhotay said:**
> I've heard (though nothing official) that they are planning on creating their own art/graphics to make it a completely FOSS game, but of course with the ability for people to import their own to play original sonic, similar to what armagetronad does. By default armagetronad looks nothing like the movie tron but there are moviepacks you can install that change the graphics and sound effects to match the original movie. This is of course highly questionable as to legality and copyrights but thats why armagetronad doesn't support/host those moviepacks themselves.

There's a good chance they will have to and if thats the case I hope they do it sooner rather then later just because I think it would be a pain to have to go back and change all the levels that they already made

---

### Post by Sslaxx on 2010-06-25
> **junebugg said:**
> This looks like it would be pretty fun. I'll have to try it sometime. I just wonder what Sega would have to say about it... Hopefully they can keep working on it. Thanks for sharing!

As far as I know they haven't said squat to [these guys]("http://www.sonicfangameshq.com/"). In fact, at least one of 'em has done work with SEGA on an official basis.

---

### Post by CharmyBee on 2010-06-25
> **Sslaxx said:**
> As far as I know they haven't said squat to [these guys]("http://www.sonicfangameshq.com/").

Are they selling games? 

OpenSonic is under a license that explicitly permits that, which goes against the use of Sonic art, trademark and characters hence its calling out for people to make that stuff.

---

### Post by PJAMA on 2010-06-26
I'm not much of a SEGA person (I'm more of a Nintendo Fanboy) I might try sometime this week.

---

### Post by metalf8801 on 2010-06-27
sorry this was posted twice

---

### Post by metalf8801 on 2010-06-27
> **donkyhotay said:**
> I've heard (though nothing official) that they are planning on creating their own art/graphics to make it a completely FOSS game...

Its in the FAQ [http://opensnc.sourceforge.net/wiki/index.php/FAQ#What_the_hell.3F](http://opensnc.sourceforge.net/wiki/index.php/FAQ#What_the_hell.3F)
> Q: What the hell? Will you create a game using Sonic or other copyrighted characters?

A: No. Have you ever played SuperTux ( [http://supertux.lethargik.org/](http://supertux.lethargik.org/) ) ? The dynamics of SuperTux is inspired in the classic Mario Bros games, but SuperTux contains only free and original user-made characters/resources. Our game is pretty much the same thing: the dynamics of it is inspired in the classic Sonic the Hedgehog games, but we're working to get this game fully free and original. Fully original characters and resources are being designed at this moment. Of course this game will have its name changed as well, but we started like this to get contributors on the Internet.

See also: Game Design Document 

They are also looking for people who can help crate new art so that its not coping the Sonic graphics 

> Artist
    Artists are responsible for the visual aspects of the game: they create the objects, animations, characters, illustrations, etc., following the Art Specification Document. 

heres more info on game design 
[http://opensnc.sourceforge.net/wiki/index.php/Game_Design_Document](http://opensnc.sourceforge.net/wiki/index.php/Game_Design_Document)

---

