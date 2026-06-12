---
title: "Doom &amp; Related Games"
date: 2010-03-16
forum: Gaming &amp; Leisure
---

### Post by deamon_knight on 2010-03-16
I stumbled across DoomsDay [http://dengine.net/](http://dengine.net/) not too long ago and I finally was able to get it running. Now I'm reminded of all the time I wasted making doom levels , so I looked into some Doom editing tools for linux. Unfortunately I haven't had much luck. This is Not TOO surprising since this is a 15 yr old game, but still. I was wondering if anyone knows of any reasonably complete tools for editing doom&etc. and making levels in Linux?

So Far I've been able to build yadex ( [http://www.teaser.fr/~amajorel/yadex/](http://www.teaser.fr/~amajorel/yadex/) ) from source after some tinkering, although it needs a node builder, and it is kinda dated. I tried to build Slade ( [http://slade.mancubus.net/](http://slade.mancubus.net/) ) however I couldn't figure out the dependencies. 

Xwad Tools ( [http://doom.wikia.com/wiki/XWadTools](http://doom.wikia.com/wiki/XWadTools) ) looks kinda promising, but I'm stumped on building. Anyone have any advice?

Thanks.

---

### Post by mastablasta on 2010-03-18
Isn't there something that would work with Wine or DosBox?

---

### Post by deamon_knight on 2010-03-18
I hadn't consider DosBOX, thats a good idea, however I was more looking for linux native software.

---

### Post by CharmyBee on 2010-03-18
Don't bother with the DOS based editors, they are way too buggy and hard to use.


Doom Builder i'm not sure if that can run on WINE, but it's what almost everyone uses these days.

---

### Post by DoktorSeven on 2010-03-18
I've had limited success with Doom Builder under Wine (version 1, v2 has too much .NET in it to be easily used from Wine) using the guide [here](http://www.doomworld.com/vb/doom-builder/44355-doom-builder-on-linux-how-to/).   Note that the image in step 5 404s now, but basically do this:
1. run winecfg
2. Under Applications tab, click Add application...
3. Browse to Builder.exe where you installed Doom Builder (c:/Program Files/Doom Builder by default)
4. With Builder.exe highlighted, click the Libraries tab
5. Click the dropdown under New override for library... and find oleaut32.  Click Add.
6. Make sure it says oleaut32 (native, builtin) under the existing overrides.  If not, highlight and click Edit, change to Native then Builtin.
7. Click Apply then OK.

(The linked image in steps 3 and 6 404 also, but I'm assuming that 3 shows running the installer with Wine and 6 just shows a pic of the successfully running application.)

It crashes occasionally but it does work.

---

### Post by jermf810 on 2010-03-18
I never got Doom to work but I do play Duke Nukem (Even better in my opinion!) Check out [http://www.cedega.com/gamesdb/](http://www.cedega.com/gamesdb/) if you are interested.

I also use ScummVM for some old LucasArts games.

---

### Post by mastablasta on 2010-03-19
Doom will work using DosBOX.
 
Also there is a port named zDoom which will make it work in linux + you can run it on high resolution settings.
 
There is also a jDoom port which really enhances graphics using openGL. Gives a whole new look to the old doom and enhances the athmosphere.
Instructions would be here i guess:
[http://ubuntuforums.org/showthread.php?t=226439](http://ubuntuforums.org/showthread.php?t=226439)

---

### Post by deamon_knight on 2010-03-21
jDoom is what I'm playing, so I'm looking for compatability with that. I found ZenNode for BSPs and Yadex works, so the basics are running. I did even fire up the basic 3 room map I made. DoomBuilder's website has been down for almost a month (its back up now) so I'm looking into that too. I'm really amazed that there aren't more Linux based tools for this, though.

---

### Post by KuriKai on 2010-05-19
Recent versions of Doomsday don't require nodes, so using ZenNode to build the BSP is unnecessary as far as Doomsday is concerned

---

### Post by formaldehyde_spoon on 2010-05-20
I used to use a DOS editor to make doom levels, it worked nicely, you could run it in DosBox.  Can't remember what it was called though...

---

