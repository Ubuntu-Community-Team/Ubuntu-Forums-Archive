---
title: "Helix or RealPlayer, with FireFox, under Breezy **** rtsp:// won't work"
date: 2005-11-23
forum: Desktop Environments
---

### Post by kitten on 2005-11-23
Please don't point me at the only thread i could find here at [http://ubuntuforums.org/search.php?searchid=2629224](http://ubuntuforums.org/search.php?searchid=2629224) it is no help at all. :confused: 

if i go to [http://www.abc.net.au/news/](http://www.abc.net.au/news/) and click on "Real Broadband" under "ABC News Bulletin" i get Helix popping up and telling me:

[COLOR="Red"]Bad Transport (rtsp://media1.abc.net.au/broadbandnews/wed_am/story10_16_9_bband.rm)[/COLOR]

which is kinda useless.

none of the tricks mentioned in that other thread have any effect at all, and this happens with both Helix and/or Realplayer, depending on how i have installed them, with "Add Programs" or "Synaptic" or "sudo apt-get install".

everything is up to date.

if i try the Windows Broadband, then i get it streaming the 1st story, using totem-xine, then it hangs.

all other type of streaming media work with one method or another, it's just this one feed that is driving me nutz. :( 

help!
Bewildered Granny.

---

### Post by kitten on 2005-11-26
:cry: nobody can help me :cry:

i will just hitch up the Zimmer Frame and shuffle off to silly-old-bat land. :KS

---

### Post by angrykeyboarder on 2005-11-26
[quote=kitten]:cry: nobody can help me :cry:

i will just hitch up the Zimmer Frame and shuffle off to silly-old-bat land. :KS[/quote]

Perhaps it's because your post got lost in the shuffle.  I didn't see the original myself.

To answer your question, forget about Helix Player, it's worthless.  Get RealPlayer instead.

---

### Post by aysiu on 2005-11-26
[QUOTE=kitten]Please don't point me at the only thread i could find here at [http://ubuntuforums.org/search.php?searchid=2629224](http://ubuntuforums.org/search.php?searchid=2629224) it is no help at all. :confused: [/quote] Sure it doesn't help. I don't see anything when I click on that link.

> 
if i go to [http://www.abc.net.au/news/](http://www.abc.net.au/news/) and click on "Real Broadband" under "ABC News Bulletin" i get Helix popping up and telling me:

[COLOR="Red"]Bad Transport (rtsp://media1.abc.net.au/broadbandnews/wed_am/story10_16_9_bband.rm)[/COLOR]

which is kinda useless. It's working for me. Have you tried installing the mplayer plugin for Firefox? That works for me, in addition to having RealPlayer.

---

### Post by Hairy_Palms on 2005-11-26
i find that copying the realplayer plugins folder to /usr/lib/win32 means mplayer can play all of reals formats, then i just uninstall realplayer :D

---

### Post by livingtarget on 2005-11-26
If you want to know which plugins you have installed type **about:plugins** in the address bar. You'd want realplayer to be in the list for sure. If totem is in there you might want to remove it. Usually the plugin files are in /usr/lib/mozilla-firefox/plugins/. You will have to do that manually. I even removed Totem, but the plugins were still there.

Just remember once you delete them they are gone :)

Mplayer-Plugin does embedded media quite well.

---

### Post by TmP on 2005-11-26
Yeah, I had the same problem.

The solution was not to install helix, but go for the newest realplayer and install it following some how-to.

It seems they mess up when are both installed.
Other than that, it could be the fact that I followed the ubuntuguide runnig on Breezy. Could've messed up some libraries with that.

---

### Post by kitten on 2005-11-30
thanks everybody, and i'll keeps those tips in mind if i ever have to real RealPlayer stuff, but actually, i found a way to do it all with totem-xine, the windows codecs, and the MediaPlayer Connectivity extension.

one point though, if anybody else tries this path, for me it only worked properly if in MPC Configuration i un-checked SmartPlay in "Configuration 1/2"

and i think i also found it hard to see a pattern because it turned out that my 60GB Maxtor hard drive was going erratic, and eventually the smoke got out; not to worry, my hardware man replaced it with a 200GB SeaGate, and i didn't lose any important data.

thanks,
Eleanor [IMG]http://www.planetsmilies.com/smilies/love/love0003.gif[/IMG]

---

### Post by 3kravinarayan on 2006-12-03
i tried to install mplayer but got this message from Add/remove programs

this cannot be installed as it conflicts with existing programs. remove conflicting program fist.

Which is the conflicting program to remove

I am still not able to install real player in the fist place

Ravi

---

