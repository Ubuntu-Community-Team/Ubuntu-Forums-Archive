---
title: "Firefox and embedded midi"
date: 2006-09-30
forum: Desktop Environments
---

### Post by russell.dexter on 2006-09-30
Hello,

Have an annoying problem here that I thought someone might be able to help with.

I am trying to get embedded midis to play in firefox, or for that matter, any browser. I installed timidity, and used mozplugger and got all the other embeds to work besides midis. The thing is - I can download a midi and play it from the command line with timidity and hear it perfectly, but when I am browsing with wither FF or Galeon I can see the little GUI that "says" it is playing at the top of every page but can't hear anything. I already did a apt-timmidity and apt-mozplugger just to make sure i had the newest files.

Any tips would be much appreciated

I am a recent convert to Ubuntu, but have been using linux off and on for the past seven or eight years. This is the first distro that I have been able to totally ditch windows for. Thumbs up to all the developers!!!

Dexter

---

### Post by infol on 2006-10-01
Hi Dexter,

it might be an issue of the plugin looking in the wrong place for the eSound Driver (esd) temp files; in Ubuntu, these are located in /tmp/.esd-1000 rather than /tmp/.esd, so try creating a symlink 
```
ln -s /tmp/.esd-1000 /tmp/.esd
``` and restar your browser and see if that works...

---

### Post by russell.dexter on 2006-10-01
Nope, that did not work. Any other ideas out there? Does anybody think this is a version bug?

Dexter

---

### Post by TheRingmaster on 2006-12-05
is there any solution to this yet?

---

### Post by rykel on 2006-12-12
I am interested to get my Firefox to play MIDI too, coz I want to hear the music on wonderofitall.com.

Please help, thanks.

---

### Post by oxman on 2006-12-27
I am having the same problem. I can play midi files with Timidity but they will not play in firefox. Any help is greatly appreciated.

---

### Post by Jose Catre-Vandis on 2006-12-29
I have embedded midi working under Dapper, well at least on my daughters neopets site, where she has embedded mp3 and midi files on some of her pages. Neopets uses the M$ tag bgsound, which needs to be translated/converted (the bgsound tag is not to standard, hence why Firefox will not recognise it as default)

Installed the following:

mozplugger for Firefox
BGM Conductor extension (which translates bgsound tags, but needs some reconfiguring to work)
but you can also use Stop Autoplay and configure settings and whitelist

timidity, freepats, pmidi for Ubuntu, all through repositories

Check about:plugins in Firefox to ensure midi is enabled by mozplugger

---

### Post by wally the duck on 2008-02-09
I have 7.10 (Gutsy) and the same issue: midi did not play in Firefox, even with timidity and mozplugger loaded.
The fix was to go to Home, turn on 'view hidden files', find the mozilla folder and delete the file that contained the plug-in registry data ( this file was not being updated when mozplugger was loaded, and deleting it causes Firefox to rewrite it next time Firefox starts, but with the updated mozplugger info).

It was a simply fix and now the midi files play.

There is a description of this 'fix' on the Mozplugger site ( [http://mozplugger.mozdev.org/](http://mozplugger.mozdev.org/) ) where under 'Notes' it says:
"You may need to delete your local $HOME/.mozilla/firefox/pluginreg.dat file for mozplugger to be enabled correctly after you update it. (It will get regenerated)."

---

