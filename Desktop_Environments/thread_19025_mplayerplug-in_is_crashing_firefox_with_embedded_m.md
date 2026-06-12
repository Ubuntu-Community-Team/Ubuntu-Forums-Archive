---
title: "mplayerplug-in is crashing firefox with embedded media"
date: 2005-03-10
forum: Desktop Environments
---

### Post by Mlehliw on 2005-03-10
I was dedicated to getting mplayerplug-in for firefox working so I installed the firefox-dev files from synaptic just in case I needed them. Then I went and got the gecko-sdk from the mozilla 1.6 build. I configured mplayerplugin with --with-gecko-sdk="..." --enable-gtk1 and moved the two *.so and *.xpt files over to ~/.mozilla/plugins

Everything was working fine then, I could watch trailers on apple just fine except the entire area where you'd expect the pause, play, stop buttons, etc. to be was blacked out. Being the cunning devil I am I decided "hey I'll just recompile this thing with a different gecko source and see if that fixes it" and rather foolishly used the first gecko-sdk for pc-solaris from this page.

[http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0/contrib/](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0/contrib/) 

After I got done compiling with that I copied the appropriate files over, launched firefox, visited apple/trailers, found a lame movie, and had firefox crash immediately. I soon realized the folly of my ways and hurried back over to mozilla and grabbed the 1.7.5 gecko-sdk and compiled again. After copying these files over I quickly found out to my dismay that firefox still crashes. I tried doing this a couple times over deleting directories and the like but it was to no avail.

Please help me.

---

### Post by lorap on 2005-03-13
hello friend!
why would't you just install vlc player?
it's ease to use and best of all i've ever seeing before.
to install it:
i.open synaptic package manager;
ii.go to the Settings----->Repositories(think i've written it right,i'm not at home right now & working in windows).mark all possible checkboxes.press Ok.
iii.press Reload button at the left apper corner.
iv.press Search button and write in "vlc" then press Ok.when the search's finished just mark it and press apply.you're done.watch movies(all) and listen to the music.
pavel

---

