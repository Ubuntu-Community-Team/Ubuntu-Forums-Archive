---
title: "KDE not starting"
date: 2005-04-10
forum: Desktop Environments
---

### Post by mikedfrwal on 2005-04-10
When i try to start a session with kde it doesnt start. anyone have this problem besides me? anyone know how to fix it?

---

### Post by josete on 2005-04-10
[QUOTE=mikedfrwal]When i try to start a session with kde it doesnt start. anyone have this problem besides me? anyone know how to fix it?[/QUOTE]
Sometimes (not always), when I switch the computer on, and after booting, KDM fails to start. This is due to the X ser ver not starting and complaining about it not finding any fonts. I believe (I haven't done any thorough tests) that this happens when I move my computer from one network connection to other (i.e., I take it from home to work). I can login and launch /etc/init.d/kdm start, and off it goes. Hope that helps!

---

### Post by mikedfrwal on 2005-04-10
[QUOTE=josete]Sometimes (not always), when I switch the computer on, and after booting, KDM fails to start. This is due to the X ser ver not starting and complaining about it not finding any fonts. I believe (I haven't done any thorough tests) that this happens when I move my computer from one network connection to other (i.e., I take it from home to work). I can login and launch /etc/init.d/kdm start, and off it goes. Hope that helps![/QUOTE]
 yea i used to have that problem as well but i dont anymore but kde wonnt start kdm starts just fine, but when i try to load kde it just has the little loading mouse pointer for a bit and my cpu light turns on. then it just stops and takes me the a world without a desktop environment

---

### Post by Manny C on 2005-04-10
Um...i think I have the sam problem.

I can (for the time being) circumvent KDE not starting up by logging into console and then starting X with su permission. That is

```
sudo startx
```

---

### Post by Manny C on 2005-04-10
Oh...i think I broke my kubuntu install when I added some *dodgy* repositories.

Will be reinstalling kubuntu tonight.

---

### Post by judyz on 2005-04-10
What is the error you are having?

I noticed when I first installed KDE on top of my Hoary that it would not load due to the fact that it could not write to the .kde directory in my home folder.  If this is the case it is an easy fix.

At a command prompt navigate to your home directory and type "sudo chmod-R 777 .kde"

I hope this helps

---

### Post by mikedfrwal on 2005-04-10
[QUOTE=judyz]What is the error you are having?

I noticed when I first installed KDE on top of my Hoary that it would not load due to the fact that it could not write to the .kde directory in my home folder.  If this is the case it is an easy fix.

At a command prompt navigate to your home directory and type "sudo chmod-R 777 .kde"

I hope this helps[/QUOTE]
 ok i tried the chmod and nothing i try to log in and it "thinks" for a while then it just stops thinking
and my error is kdm starts out like it wants to go to the login in screen and it just doesnt and when i can get it to at least log in kde wont load itll act like its loading and y cpu light goes on then all of a sudden everything stops

---

### Post by Manny C on 2005-04-11
[QUOTE=mikedfrwal]ok i tried the chmod and nothing i try to log in and it "thinks" for a while then it just stops thinking
and my error is kdm starts out like it wants to go to the login in screen and it just doesnt and when i can get it to at least log in kde wont load itll act like its loading and y cpu light goes on then all of a sudden everything stops[/QUOTE]

I have the same problem...did you try to rectify the problem using the tip in my previous post on this thread?

Also, what seems to have triggered this system breakage? As I previously mentioned, I think adding some dodgy repos and updating packages from there may have broken some of my system...maybe it was me adding a superuser password. I don't know yet.

---

### Post by mikedfrwal on 2005-04-11
[QUOTE=Manny C]I have the same problem...did you try to rectify the problem using the tip in my previous post on this thread?

Also, what seems to have triggered this system breakage? As I previously mentioned, I think adding some dodgy repos and updating packages from there may have broken some of my system...maybe it was me adding a superuser password. I don't know yet.[/QUOTE]
wellll it was a fresh install of the kde desktoip and nothing has helped so im stuck here

---

### Post by judyz on 2005-04-12
Interesting...

It is not having a superuser password that does it.  This was the first thing I did to my system and I use "su" frequently without any problems.

If this is occuring during the time when KDM is loading I am wondering if KDM has gotten fouled up?  Has anyone tried using apt-get at the command line to remove and reinstall it?

The most likely source of the problem though is probably Video Drivers.  Since they would be initalizing around this point and they are often the biggest source of fustration in linux.  What video card are you running?  Have you tried updating the drivers?

---

### Post by mikedfrwal on 2005-04-12
[QUOTE=judyz]Interesting...

It is not having a superuser password that does it.  This was the first thing I did to my system and I use "su" frequently without any problems.

If this is occuring during the time when KDM is loading I am wondering if KDM has gotten fouled up?  Has anyone tried using apt-get at the command line to remove and reinstall it?

The most likely source of the problem though is probably Video Drivers.  Since they would be initalizing around this point and they are often the biggest source of fustration in linux.  What video card are you running?  Have you tried updating the drivers?[/QUOTE]
 ok its not my drivers most likely kdm is fouled up i use gdm just fine
i have a radeon x800 pro with the most updated drivers im bout to just give up and reinstall and then im goin to trey again

---

