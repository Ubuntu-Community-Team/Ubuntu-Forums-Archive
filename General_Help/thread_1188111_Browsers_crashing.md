---
title: "Browsers crashing"
date: 2009-06-15
forum: General Help
---

### Post by GabrielsHorn314 on 2009-06-15
Hey guys,
   I have been having some trouble with mozilla firefox recently, so I decided to remove it and download a new one. Everything was refreshed and completely new but it continued to shut down for apparently no reason. Also, I can no longer play videos on most pages. (Youtube seems to be about the only one that works fine). Since I was having these problems I just decided to use opera and midori in the meantime, but they are just crashing as well. If anyone has any insight as to why it would be doing this, or how to solve the proble please let me know. Apart from the videos not working and infrequent crashing of browsers ubuntu works fine and I have no overall problems. Thanks a lot for any help you guys can give.

Cory

---

### Post by Ceiber Boy on 2009-06-15
i'm no expert but i had a SIMULAR problem, the explanation i had given to me was that the web pages were using invalid script commands! the good news then is that their is notheing wrong with firefox, but the bad news is that their is no fix

---

### Post by GabrielsHorn314 on 2009-06-15
It happens far to frequently for it to be a problem like that in my opinion. Especially since it happens with sites that I should have no problem booting up and that I have had no problems loading in the psat. for example the us epa website crashes firefox pretty much every time, which doesnt make sense to me. did u not do anything, and just delt with the crashes?

---

### Post by ajgreeny on 2009-06-15
If you are using *mozilla-mplayer* to view these files and videos, or erven just listen to audio, I suggest you uninstall it and try using *gecko-mediaplayer* instead.  I was having what sounds like a similar problem watching apple.com movie trailers, and listening to the BBC here in UK.  Asd soo as I clicked on the watch or listen live button the whole browser crashed with no useful clues even when started from terminal, just "Segmentation Fault" - very helpful!  So I changed the plugin, and no further problems.

If you are not using mozilla-mplayer, then I have no idea, other than flash, but as you-tube is OK I asume flash is working well for you.

---

### Post by Vostrocity on 2009-06-15
How many tabs do you have open on average? I usually use about 50 tabs at a time and it crashes a lot. But I can't fault the browser for that. :D

---

### Post by GabrielsHorn314 on 2009-06-15
no more than 5. 

50, damn, i would have no idea how to use that many tabs.

---

### Post by GabrielsHorn314 on 2009-06-15
ajgreeny:
 Thanks for the advice, and here are the plugins currently using:
  Default plugin
  Demo print plugin for unix
  DivX web player
  Java Plug-in
  Quicktime plugin
  Shockwave flash
  VLC multimedia plugin
  Windows media plug-in 10

but seeing as the problem occurs with all of my browsers, i doubt its a problem simply occuring in firefox. I wondered if my settings were causing browsers to shut down when something occured that i was not aware of? but i dont really know.

---

### Post by ajgreeny on 2009-06-15
You don't actually say if you have mozilla-mplayer installed but from your list of plugins it is possible you do, and I would still suggest you get rid of it if it's the one you use for the divx, quicktime and windows-media plugins.  I think the same package is used for other browsers as well so it could be the cause of your problem. Give it a try to see, you can always go back if necessary.

The actual file used will be listed along with the generic name eg mine says:-

DivX Browser Plug-In 
File name:  /usr/lib/mozilla/plugins/gecko-mediaplayer-dvx.so
[Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 0.9.4

etc etc for the others, showing it is gecko-mediaplayer, not mozilla-mplayer which I have always used without problems until jaunty.

---

### Post by GabrielsHorn314 on 2009-06-15
I dont see that it says mozilla player anywhere. under divX it just says: " DivX web player version 1.4.0233"

under some of the others  (Quicktime, VLC, Windows) it has : " The totem 2.26.1 plugin handles video and audio streams"

---

### Post by GabrielsHorn314 on 2009-06-15
I did find this in Opera for plugins:

DivXÂ® Web 
Playervideo/divx	divx
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so

i saw mozilla, as you mentioned. but its totem, and not mplayer.

---

### Post by ajgreeny on 2009-06-16
OK, it does not sound as if you have mozilla-mplayer for your media, so I don't think I can suggest any other things to try, unless you want to attempt removing the totem-mozilla plugin and adding mplayer and gecko-mediaplayer just to try it out.  As I said, you can always go back if you prefer the setup as you have it at the moment, but as that doesn't work anything else that does would be better, yes?

---

### Post by GabrielsHorn314 on 2009-06-16
I downloaded gecko from synaptic. how do i get firefox to pick it up?

---

### Post by GabrielsHorn314 on 2009-06-16
ok, i got mozilla to pick it up, but unfortunately no luck.still cant play a majority of videos.

---

### Post by GabrielsHorn314 on 2009-06-16
Now by saving the files and trying to open them up seperately in a movie player or VLC i get this error:

GStreamer encountered a general supporting library error.

any ideas?

---

### Post by ajgreeny on 2009-06-16
Not really, sorry.  I have always got rid of the totem plugin for firefox because I think it is not very good, certainly not as good as mozilla-mplayer used to be, anyway.  I also always add totem-xine and use that rather than totem-gstreamer as it is much better at playing DVDs than the gstreamer version, in my opinion.

I think your error message is perhaps occuring because you have messed with totem, but I can't say for certain.  I think I have to withdraw here and let others with more knowledge try and help you.  Assuming you system was a default setup before I suggested these things which have not worked, it may be worth undoing all thast you have done and reinstating the programs you've removed, etc etc.

Sorry if this is no help, but I was hopeful it would be.

---

### Post by GabrielsHorn314 on 2009-06-16
well thanks for the help any ways.

---

