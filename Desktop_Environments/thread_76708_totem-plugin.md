---
title: "totem-plugin"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Hairy_Palms on 2005-10-15
i have a problem with the totem plugin for firefox, when i go to a film it just stalls and wont play, i installed the mplayer plugin which worked in hoary but firefox still uses the  totem plugin any idea on how to get totem working or removing only the plugin?

---

### Post by Hairy_Palms on 2005-10-15
noone?

---

### Post by entvex on 2005-10-15
do you have all gstreamer ?

---

### Post by Toddy on 2005-10-15
To get rid of the Totem plugins in Firefox, go to /usr/lib/mozilla-firefox/plugins and move the libtotem*.* files.  Check that the plugins are gone by doing an about:plugins in Firefox.

---

### Post by joelito on 2005-10-15
I manually deleted all libtotem files from /usr/lib/firefox/plugins

To get there

alt+f2,

run, gksudo nautilus,

Then just browse to the location or ctrl+L to browse directly

---

### Post by Hairy_Palms on 2005-10-15
thx that worked, i wish totem plugin worked though,

---

### Post by nix4me on 2005-10-15
I had the same problems.  Totem seems to be broken in Firfox.  Gstreamer too.

The only thing I have found that works in Firefox is mplayer-plugin.

It's ashame that once again multi-media integration is mostly crap in Ubuntu.  Maybe it will get better soon.

nix

---

### Post by Chuckaluphagus on 2005-10-16
[QUOTE=nix4me]I had the same problems.  Totem seems to be broken in Firfox.  Gstreamer too.

The only thing I have found that works in Firefox is mplayer-plugin.

It's ashame that once again multi-media integration is mostly crap in Ubuntu.  Maybe it will get better soon.

nix[/QUOTE]

The fix is to replace totem-gstreamer with totem-xine.

I had the same problems as the rest of you.  In my case, It wasn't totem or the totem integration with Firefox, it's the base media player underlying totem.

Totem is just a front-end that gives you a consistent interface regardless of the media player that's actually handling the file.  The default for Ubuntu is gstreamer, and in my experience gstreamer, well, it's not particularly good.  At all. (If your experience with gstreamer has been better than mine, all power to you.)

If you go into Synaptic and run a search for "totem-xine", you can install that as a replacement for totem-gstreamer.  If you don't have xine already, it will install the necessary packages for that too.  Xine handles video files much better than gstreamer, and with totem-xine the integration into Firefox works as well.  If you get the proper codecs for Quicktime, WMV, DivX, etc. (check out Easy Ubuntu at [http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23)](http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23)), it'll handle all of them.

Hope this helps you all.

---

### Post by Aphorism on 2005-10-16
Here is a relevant post for you.  It involves mozplugger which permits just about any app to embed into moz based browsers.  

[http://www.ubuntuforums.org/showthread.php?t=17727](http://www.ubuntuforums.org/showthread.php?t=17727)

Good luck...

---

### Post by Hairy_Palms on 2005-10-16
> The fix is to replace totem-gstreamer with totem-xine.

I had the same problems as the rest of you. In my case, It wasn't totem or the totem integration with Firefox, it's the base media player underlying totem.


i already had totem-xine, its one of the first things i do and it still didnt work

---

### Post by mrmcctt on 2005-10-16
Not sure if this would help you or not.  Go to [this thread]("http://www.ubuntuforums.org/showthread.php?t=66563") and check it out.  It's a very nice utility for setting up your system including firefox plugins, media players and codecs.

Additional codecs not included in the Automatix install can be dowloaded in the essential pack at [this site]("www.mplayerhq.hu/").  (Their site appears to be down at the time of this posting but this is where I've seen the codecs pack at)

---

### Post by mostwanted on 2005-10-16
I have the same problem. Totem with gstreamer crashed my firefox when I closed the tab (and nothing happens anyway), Totem with xine just doesn't work, nothing happens.

I think I'll get rid of this plugin... :( sucks, I had been looking forward to this in the Gnome 2.12 release.

EDIT: Looks like they've improved on the Mplayer plugin, I'm not complaining much then ;) They got rid of the blue amateurish design and replaced it with actual widgets and it's now possible to stop, pause and skip through sound/video. Now the only thing we need is better support for streaming.

---

### Post by Hairy_Palms on 2005-10-16
i wrote a script to automatically replace totem-plugin with mplayer-plugin ill post it below

---

### Post by kayas80 on 2005-10-17
[quote=joelito]I manually deleted all libtotem files from /usr/lib/firefox/plugins

To get there

alt+f2,

run, gksudo nautilus,

Then just browse to the location or ctrl+L to browse directly[/quote]

Sweet! Now Firefox works with mplayer and I know how to browse as SUDO. :cool:

---

