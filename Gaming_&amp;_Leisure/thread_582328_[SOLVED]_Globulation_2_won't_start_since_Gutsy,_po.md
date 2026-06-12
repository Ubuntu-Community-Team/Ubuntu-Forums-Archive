---
title: "[SOLVED] Globulation 2 won't start since Gutsy, possibly my fault"
date: 2007-10-19
forum: Gaming &amp; Leisure
---

### Post by keyboardashtray on 2007-10-19
Globulation 2 won't run for me now since I upgraded to Gutsy.

This is what I get when I try to start it from the terminal:

```
glob2: error while loading shared libraries: libboost_thread-gcc-mt-1_33_1.so.1.33.1: cannot open shared object file: No such file or directory
```

I've tried uninstalling (complete removal) from Synaptic, and reinstalling.

I'm guessing it might be related to how, before Gutsy, there was an update to Globulation so I downloaded and compiled the new source version. There were a couple bugs for me, though, so I tried removing it through Synaptic, and reinstalling the old version from the repos, but I couldn't figure it out. Whenever I would run it, it would always run the latest version, not the version from the repos (which is what I wanted now).

Any ideas?

---

### Post by donkyhotay on 2007-10-20
I haven't upgraded to gutsy myself but I am familiar with globulation2. According to your original error message it's having problems with a file within the boost library which is a dependency of globulation. Check synaptic and make certain you have libboost and libboost-devel installed. I would also check for something along the lines of libboost-thread as well. I can't remember if libboost-thread is automatically installed with libboost and with all my linux systems down for the school season (@#$%ing windows admin classes) I can't double-check synaptic myself but I think it isn't (and most likely your problem). Once you have that all that installed globulation2 should work if you get it from the repos and it was working earlier. If that doesn't work then I would recommend downloading *all* the dependencies listed here:
[http://globulation2.org/wiki/Download_and_Install](http://globulation2.org/wiki/Download_and_Install)
including the dev versions (won't work without them) and compile from source (would recommend compiling from source anyways for latest version). If you still run into problems post your problems onto the globulation2 forums and one of the more current developers will be along in a few days or so.

---

### Post by keyboardashtray on 2007-10-22
> **donkyhotay said:**
> I haven't upgraded to gutsy myself but I am familiar with globulation2. According to your original error message it's having problems with a file within the boost library which is a dependency of globulation. Check synaptic and make certain you have libboost and libboost-devel installed. I would also check for something along the lines of libboost-thread as well. I can't remember if libboost-thread is automatically installed with libboost and with all my linux systems down for the school season (@#$%ing windows admin classes) I can't double-check synaptic myself but I think it isn't (and most likely your problem). Once you have that all that installed globulation2 should work if you get it from the repos and it was working earlier. If that doesn't work then I would recommend downloading *all* the dependencies listed here:
[http://globulation2.org/wiki/Download_and_Install](http://globulation2.org/wiki/Download_and_Install)
including the dev versions (won't work without them) and compile from source (would recommend compiling from source anyways for latest version). If you still run into problems post your problems onto the globulation2 forums and one of the more current developers will be along in a few days or so.

Hey donkyhotay!  I talked to you briefly over at the glob2 forums too (Farmer Glob, had the issue with the wanting to downgrade again). Sorry to hear about the classes stealing your computers for the year - man thats a bummer. They don't want you running a dual boot even huh?  So you're one of the devs for Glob 2 then - awesome game man. 

Yeah, you know I really think the changes for the most recent version look cool, I mean it got me to compile my first program, which is a pretty big step for me! But there were some issues for me, it was crashing when I'd change the map overlays, and when I'd exit, etc., so thats why I decided to try and go back to the version I had originally gotten from the repos. 

I followed the directions you gave over at the glob2 forums, I reinstalled from the repos, but when I'd run it, it would still show it as the most recent version in the bottom left corner.

To current: Now since Gutsy its been doing what I mentioned above. So anyway, I checked, and I have the libboost, libboost-devel, libboost-thread. I tried reinstalling them, still getting the error message though. I haven't tried running through the other dependencies manually like when I compiled. Anyway, could the package that is currently in the repositories possibly be made incompatible by the upgrade? Does that happen sometimes? This is the first upgrade I've been through, so I don't know what can happen, I'm just assuming sometimes a program here or there slips through the cracks. 

But it is just as likely I did something when I was experimenting on how to downgrade. I tried double clicking mkuninstall, etc., deleting files here and there probably. So thats why I don't want to potentially flag the glob2 package as having a bug when it's likely something I did.

Anyway, no biggie I guess, I guess I could try the source package again. I'll probably hold off, I'm debating doing a fresh Gutsy install from the livecd as this was my first few months running GNU/Linux so I'm sure I've made a mess here and there. If I go that route I can try the repo version again, and if that fails then I'd give the source package a whirl again.

---

### Post by donkyhotay on 2007-10-23
Oh hey farmer glob I remember you from the glob2 forums. Thanks for the compliment but I'm not one of the lead developers. When I was active I mostly did minor things like bugfixes (my most notable feature is the unit settings) and while I am still on the mailing list and keep track of the project I haven't done anything in about a year now. Anyways... it  isn't so much a matter that they don't want me to dual-boot as much as *I* don't want to dual-boot. I consider dual-booting a waste of time since I can work equally well in either enviroment. Only problem is I have difficulty troubleshooting something I don't have. You reminded me though that I have a rarely used laptop that still has ubuntu (feisty) on it. I did some experimenting with it and found that installing with scons places the binary in 
/usr/local/bin/
while synaptic installs it in
/usr/games
I had assumed they installed at the same location and they would overwrite each other. Since they don't, your system just loads the one it finds first (the source version in this case). In order to play the old version make certain it's installed via synaptic and then delete /usr/local/bin/glob2
I would also delete
~/.glob2
as well to make certain in case there are incompatibilities within preferences or saved games between the two versions. Tomorrow I'm going to upgrade my laptop to gusty and see if there are any major problems with glob2 and let you know what I run across.

---

### Post by keyboardashtray on 2007-10-24
Sweet! That did the trick - it's up and running now :guitar: They must have updated the version in the repos, because it has some of the features that were in the newer release I had tried. It says 8.23, not 9.1... I don't remember what number version I had first, but it didn't have the little swirling icons in the area paints, for example. Cool -

I really appreciate you taking out the old laptop and digging around the files to see whats up. =D> I hope it wasn't too much trouble. Don't go out of your way to upgrade tomorrow for my sake, I'm up and running now - but maybe you want to check out Gutsy just to see whats new with 7.10. 

Well, I'm gonna go get a game in - been a few weeks. Thanks again!

---

### Post by donkyhotay on 2007-10-24
Well, I needed to test out gutsy anyways since it's going onto my desktops after the term ends. Back to your original issue, I'm not certain why you weren't able to compile from source. I upgraded to gutsy, made certain I had the latest glob2 source code from mercurial and then recompiled glob2 from source. It compiled, installed and played perfectly. I'm guessing you must have a missing library somewhere that is preventing you from compiling from source. I've noticed that sometimes the scons error messages aren't always accurate. Your probably missing the development version of some library besides one of the libboost libraries since you already checked those. But if your content with 8.23 and we've confirmed there isn't anything inherintly wrong with glob2 on gutsy then I won't worry about it.

---

### Post by keyboardashtray on 2007-10-25
Well, since yours was working fine, I decided to try the newer from-source version again. This time, compiling was a breeze, I ran SCONS, it went through every thing, and then I ran SCONS install, and it installed.  I've played a couple games, the first one went OK, then I turned on the fertility overlay, and it was ok, I turned it off, then I laid an attack flag, and it crashed, and it also froze up the desktop too (I had to CTRL+ALT+backspace). I don't know how to find an error message when that happens, sorry :redface: I hadn't run it in terminal, either. Is that the only way to retrieve error data when it crashes, to have run it from the terminal in the first place?

My second game went great (wow were the AI's tweaked? 2 AICastor enemies nearly crushed me, and they started hitting me with ground-attack scouts, never seen them do that)  - but I didn't use the fertility overlay. I hate to blame that, it might have been a coincidence, but the last time I was running the from-source version, it seemed to trigger the same style of crash, freezing the desktop. It would also do this from the editor (previously, first time round with the from source 9.1). That I haven't fooled around with yet.

Maybe you were right about missing some files the first time around. But would it run at all with something missing? It was my first compile, and it went pretty sloppy for me at first. I'd run SCONS, and it would stop, tell me it didn't have something, so I'd grab the thing it said I was missing, then run it again, and each time it would stop right when it got to something I didn't have. Until I got to I *believe* libboost thread: it would tell me that I didn't have that, but instead of stopping like it did before for each other thing I was missing, it would run through a ton of extra stuff, and then tell me it failed. Even though I'd installed (I'm assuming) libboost through Synaptic, it would do that. So, first I followed the link from Glob2 and compiled liboost stuff from source, it still was failing, telling me that it was missing, running through some extra processes, and then fail. Then I got build-essential. After I got build-essential, it ran through the list, I *believe* still said libboost was missing, but then it charged ahead through that process afterwards, and this time it didn't fail. I then ran SCONS install, and it worked.

I know thats some sloppy info there, heh, and it doesn't help I'm not positive about the messages, etc. I realize. Just trying to paint a picture of what it was like first time around, so maybe you'd get an idea of if it was a sloppy install.

I should probably take anything else over to the Glob2 forums, I just figured since I had your attention here I'd get your opinion before I start confusing everyone else over there with bugs, etc. that might just be from my install.

But, I'm back in the game, so I've jumped the biggest hurdle. I'll have to try and recreate some of the maps I had made, and maybe submit a couple eventually.

---

