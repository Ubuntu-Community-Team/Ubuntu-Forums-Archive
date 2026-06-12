---
title: "Compiz Fusion Causing Screen Saver Oddness"
date: 2007-09-26
forum: Desktop Effects &amp; Customization
---

### Post by Locutus_of_Borg on 2007-09-26
I'm using Kubuntu with compiz fusion working fine, but when my screen saver activates it only displays in the lower right 75%  of the screen.  
________
| .......... |    
|...._____|
|....|......| 
|.__|____|

...thats my ascii version (ignore the periods) of what im talking about, the screen saver only takes effect in the lower right box


also for a while it started displaying my GNOME screen saver even while in a KDE session (i would actually like to be able to do this if theres a way to set that up)


one other issue is all of the screen saver options that have GL at the end, do not work.

thanks for any advice/suggestions

---

### Post by jyneo on 2007-09-27
i'm having this exact same problem only i'm using openSUSE 10.2

somebody told me there was a patch to fix it but it didn't work for me. the forum is down right now so i can't look at it but i know the file that needed to be patched was lockprocess.cc 

there's no lockprocess.cc on my system so i couldn't patch it obviously but it could work for you maybe 
i guess just search google for lockprocess.cc patch?

sorry i couldn't give you anymore information... good luck on getting this issue resolved... i know its annoying the hell outta me :lolflag:

p.s. while i was typing this reply my screensaver came on on the computer that has compiz-fusion and it was normal... YAY! so i log in and click lock session and it goes back to only taking up the bottom right 75% of the screen... GRRRR... God's a comedian...

---

### Post by Locutus_of_Borg on 2007-09-27
just found this: [http://www.linux-noob.com/forums/index.php?showtopic=2504&pid=9274&mode=threaded&start=](http://www.linux-noob.com/forums/index.php?showtopic=2504&pid=9274&mode=threaded&start=)

havent tried it yet since i have to use windows to dial-up (modem configuration is a bitch)

---

### Post by jyneo on 2007-09-27
it works! wow thanks. i've been up all night trying to fix that! :popcorn:
time to go to bed lol
thanks again

EDIT: okay, well it works most of the time when the screensaver starts up on its own. but when i manually lock session it is still offset 75% down and right... i guess when i lock session kde is still using its own screensaver instead of xscreensaver? to test this i'll set the screen savers for two different ones and see if when i lock session the kde screensaver pops up or the xscreensaver. i'll post back on here with the results.

---

### Post by Locutus_of_Borg on 2007-09-27
no problem :)

it worked for me as well

---

### Post by jyneo on 2007-09-27
yep, when i use lock session from kde its still using kscreensaver... DAMN IT! to lock the session with xscreensaver i'd have to run xscreensaver-demo => file => lock the screen
there must be an easier way to do this. maybe i can make an executable on my desktop that locks the screen through xscreensaver when i click it?

---

### Post by jyneo on 2007-09-27
made an executable on my desktop simply with the command
xscreensaver-command -lock
so now when i want to lock my screen i just click that and works like a charm :)
i don't use gnome so i don't know if this problem still exists for you but if it does this is an easy fix ;)
i'm also not sure how you make executables with gnome, so i can't tell you exactly how... you probably know anyway (if i can do it anyone can) basically i made a Link to Application and in the Application tab i typed xscreensaver-command -lock on the Command line and named it Lock_Session.

---

### Post by Locutus_of_Borg on 2007-09-28
i use KDE primarily as well

I dont have much cause for locking my screen, though, since my wife is the only other person to touch my computer, and thats only when she's not on hers for some reason, so i just set it to password prompt after 30 minutes of inactivity

---

### Post by jyneo on 2007-09-28
i love being able to lock my screen. mostly on my laptop when i'm at school or work and i need to lock it out on impulse. instead of having to wait for the screensaver to pop up or log out completely.

lol, that was one of my main reasons for falling in love with linux >_< can't do that on windows without 3rd party software like Montior Control

---

### Post by Locutus_of_Borg on 2007-09-28
errr...windows key + L locks the screen in Windows

im sure there is an equivalent in linux, but i dont know as i am very inexperienced with it

---

### Post by Locutus_of_Borg on 2007-09-28
yeah
ctrl+alt+L locks your current session

---

