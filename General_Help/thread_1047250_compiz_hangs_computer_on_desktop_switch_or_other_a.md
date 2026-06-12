---
title: "compiz hangs computer on desktop switch or other activity"
date: 2009-01-22
forum: General Help
---

### Post by LordIshamael on 2009-01-22
hey im using kubuntu 8.10 with kde 4.2
whenever i try to switch a desktop, or do something else like open more than a few programs while running compiz, the computer hangs
it doesnt respond to ctrl-alt-backspace even, i have to hard reboot it
once, i was running vlc and i could still hear the video playing even though nothing was changing on screen
this problem had been there in 4.1 as well

i also run compiz in xfce, and have tried it in gnome, no problems faced there

any idea why this is happening and how to fix it? id prefer to keep running compiz rather than just keeping with kwin

as an aside, is it possible to run compiz as the wm while keeping kwin's window decorations?

---

### Post by LordIshamael on 2009-01-28
bump?
just checked, and its not just in the rc, kde 4.2 proper is the same
going to try reinstalling compiz again now, but any help would be appreciated

---

### Post by LordIshamael on 2009-01-28
i think i found the problem
compiz-kde package is not being installed as it depends on libplasma2, but whats installed is libplasma3
trying to install libplasma2 results in adept wanting to remove libplasma3 along with a host of kde apps and stuff, so i didnt do it

i tried to install a plasma widget in the 4.2 rc (playwolf) and it had also said that it required libplasma2 to install, so i couldnt install it

any idea if theres a workaround for this?

---

### Post by shankar556288 on 2009-01-28
i have a more serious problem with compiz. after installing the Compiz Config manager recently in my ubuntu 8.10, i added some effects and as a result, now the display goes totally black as soon as it is loaded. so i am unable to use any option and i am posting here using the Guest session only. So need urgent help on how to fix the problem. i am unable to use the GUI totally in the user mode. 

            Thanks in advance!!!

---

### Post by LordIshamael on 2009-01-28
osx widgets and google gadgets dont install either...
i download the package files, try to install the packages but they dont get installed
with google gadgets, the installer says it couldnt install the file, but not with the widgets
and im only seeing very few widgets downloadable on the listing from the add widgets dialog, despite there being so many more on kde-look.org

whats going on? why is kde so wierd? i cant even install anything else, like login themes or anything, through that add new themes dialog or otherwise

---

### Post by Promethalus on 2009-01-29
seriously vague, get all that stuff reinstalled again, or switch to blackbox or enlightment, much more sleeker, and trustworhty, and what did you use? GTK? Not emerald theme manager? never heard of it . . .

---

