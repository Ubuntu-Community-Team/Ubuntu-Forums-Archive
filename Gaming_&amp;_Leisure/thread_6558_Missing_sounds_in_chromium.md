---
title: "Missing sounds in chromium"
date: 2004-11-29
forum: Gaming &amp; Leisure
---

### Post by linny129 on 2004-11-29
I installed it via apt-get. I have music, but no other sounds. All my other games work fine. are there additional files that need to be installed with chromium??

---

### Post by jdodson on 2004-11-29
i remember someone else having the same problems, do a forum search for chromium.

---

### Post by linny129 on 2004-11-29
[QUOTE=jdodson]i remember someone else having the same problems, do a forum search for chromium.[/QUOTE]

Been there, done that. The only post I found on my search was the one hoary area, and it's not the same issue.

Edit: Well I did find this comment in a thread listing games available for linux:

"Kill all sound daemons like esd or artsd before playing if you want sound"

What is the command to do this, or can I just mute them through the sound mixer?

---

### Post by HungSquirrel on 2004-11-29
If you have music, then you don't need to kill sound daemons.

I too lack sound effects other than music.

---

### Post by linny129 on 2004-11-29
Killed the esd process - no good still :(

---

### Post by linny129 on 2004-11-29
[QUOTE=HungSquirrel]If you have music, then you don't need to kill sound daemons.

I too lack sound effects other than music.[/QUOTE]

Well then that rules that out..

---

### Post by linny129 on 2004-11-29
after running it in a terminal, I noticed I do get this error even though the game runs: 

ATTENTION!! Could not load alAttenuationScale
alAttenuationScale == 0. Kludge it.

Looks like it is related to openal somehow, but I am not sure how to fix it.

---

### Post by HungSquirrel on 2004-11-29
This issue affects all games for me that use OpenAL.  I get no sound effects in UT2004 or in cedega games.  It didn't happen before I did the Hoary upgrade.

Devs, take note!  8)

---

### Post by Borgmeister on 2004-12-02
I have the same problems, ina ll my games, no sound whatsoever, abuse, chromium, tux racer, frozen-bubble, pingus, u name it, it wont make a sound, however, totom-xine plays my files, music or video with all sound present.n I have trawled the net in vain, and still nothing works.

---

### Post by linny129 on 2004-12-02
Well I have gone back to SUSE for now - at least I don't have any sound problems with it. I tried Doom Legacy under UBUNTU and couldn't get music. However it runs fine under SUSE and so does chromium

---

### Post by linny129 on 2004-12-03
[QUOTE=linny129]Well I have gone back to SUSE for now - at least I don't have any sound problems with it. I tried Doom Legacy under UBUNTU and couldn't get music. However it runs fine under SUSE and so does chromium[/QUOTE]

I saw this in the  Doom legacy forum - may help someone who is trying to run that:


"You also need a set of patches for Timidity to work. On Debian the package is called timidity-patches or somesuch. Not sure what it is on Ubuntu"

---

### Post by budda on 2008-03-07
The second variant solved the problem for me: [http://ubuntuforums.org/showpost.php?p=3152472&postcount=8](http://ubuntuforums.org/showpost.php?p=3152472&postcount=8)

---

