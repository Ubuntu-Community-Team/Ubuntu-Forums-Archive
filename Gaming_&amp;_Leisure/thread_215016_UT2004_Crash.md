---
title: "UT2004 Crash"
date: 2006-07-13
forum: Gaming &amp; Leisure
---

### Post by vem0m on 2006-07-13
hey guys its me :)

Anyways i am playing UUT2k4 and it crashes out of the game sometimes. i am running it with the 3369 patch, its usally right b4 i start a level i goto hit play and it crashes this last time my mouse out of game after crash was froze so i had to restart computer. any ideas what is causing this?

---

### Post by xeta on 2006-07-13
try to run ut2004 from the commandline. Once it crashed, post the output of that terminal window here for more help. It may be that you do not have access to the cache directory but, lets see what the output is first.

---

### Post by vem0m on 2006-07-13
> WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Signal: SIGSEGV [segmentation fault]
Aborting.


Crash information will be saved to your logfile.
Segmentation fault

that is what i get

---

### Post by xeta on 2006-07-13
Go download the latest patch for ut2004 and that should help you. This error should not be crashing your client.

---

### Post by vem0m on 2006-07-13
yes but its not the ATi as nvidia does tha same thing as i found searching the web but i have not found a solution also all my system specs are in my signature under my posts :P

---

### Post by xeta on 2006-07-13
Paste the log file that shows the error as well.

---

### Post by vem0m on 2006-07-13
[http://paste.ubuntu-nl.org/17943](http://paste.ubuntu-nl.org/17943) look there for the log output

---

### Post by vem0m on 2006-07-13
also it seems it happens on most games running the UT game engine such as Americas Army, UT2k3/4 to name a couple so i dunno i think i am one of the instances that i am just screwed dunno tho but i might try running it thu cedega and seeing if that works any better

cedega failed install won't start

---

### Post by vem0m on 2006-07-13
ok i know i am not the only one affected by far can anyone else help? i already looked and tried various other crap like deleting the saved settings ETC and each crash while it happens now so quick i cannot play the game the log says differant crap along with that same crap so my next question is has anyone been able to fix this or am i stuck with Quake 3?

---

### Post by xeta on 2006-07-13
are you running ut2004 as root? or user? Try root just for the heck of it.

---

### Post by vem0m on 2006-07-13
i have tried both and both have crashed

---

### Post by xeta on 2006-07-13
I'm assuming you have the latest patch?

---

### Post by vem0m on 2006-07-13
yes as stated before 3369

---

### Post by vem0m on 2006-07-14
well seems i have fixed it i will tell u what i did to help all those who might be having same issues

Uninstall it with the Loki Uninstaller
Delete Both the UT2004 and .ut2004 directories from your home directory(if that is where u installed it at)
Reinstall it
goto [http://liflg.org/?catid=6&gameid=17](http://liflg.org/?catid=6&gameid=17) and download the mega pack and install it after that everything should be up to date and no crashing ENJOY!

---

### Post by xeta on 2006-07-14
Very odd fix. Uninstall and re-install? Whats the difference between regular install and the mega pack?

Glad to see it working and thanks for posting the fix. I'm sure alot of people will benefit by your hard work.

---

### Post by vem0m on 2006-07-14
well u do a regular install then u update it and add the extra content with megapack so not only does it update it for u it installs UT2004 megapack
> This latest patch from Epic Games will give you everything you need to update UT2004 to the most current version, including nine new Deathmatch, Assault, and CTF maps. The patch also includes all of the content from the first (Editor's Choice Edition) bonus pack for UT2004.

i am guessing when ppl are doing amanual update as i did(copy files from the update into the UT2004 folder) it messes up but when i used the mega pack to update it and add content it worked

---

### Post by Curlydave on 2006-07-14
It sometimes crashes on me too - as in complete system lockup. No idea why, but it will often do it when clicking "low sound detail".

---

### Post by vem0m on 2006-07-14
well i don't mean system lockup however u might make sure no other app is using sound at that time as UT2004 hates that

---

