---
title: "3 questions"
date: 2005-06-07
forum: Desktop Environments
---

### Post by arendald on 2005-06-07
1. How to switch to administrator mode, when logged as user, on kde control center ?

Tried the user password (I'm forced to use since even if I created a root password, kde does not care for it and only shell can handle it apparently), does not work, the window goes back to the blue start page. If I try the root password I have created, it says 'Incorrect password' which is logic even if it's beyond me why root password is totally ignored on kde.

Anyway, I just want to modify some stuff on kdm.

2. Every time I start kaffeine, there's a little window popping up in the middle of the screen and vanishing right away, I can't read it and have no clue of what it is because it is way too fast. 

Does anyone know what that is ? Kaffeine version is 0.6 on kde 3.4.

3. I use few gtk apps but for some tasks, we have very little choice from the kde side. Anyway in order to have a coherent look and feel I use QT-GTK-engine stuff which makes the gtk apps use the kde themes/fonts. Works okay.
My question is : how to get rid of the icon on the buttons of gtk apps (I don't use any icon on button under kde) ?

Thank you for your patience and help ;-)

---

### Post by ltmon on 2005-06-07
I think the kcontrol issue is fairly well reported.  

The workarounds I know are to use the "settings" kioslave (in your system menu you should see a "Settings" entry) rather than the actual kcontrol.  This works fine.

The other one is to actually start kcontrol with "sudo kcontrol", which is a bit annoying as well.

---

### Post by arendald on 2005-06-08
For my question 1, you were right the system menu/settings works fine. I also tried sudo kcontrol and surprisingly it worked too. I was surprised because I did try with su root then kcontrol and it didn't work. Sudo kcontrol does work. I guess they don't work the same way. Thank you anyway ;-)

Still looking for answers to 2 et 3 ;-)

---

### Post by geearf on 2005-06-08
when you do sum then kcontrol it mostly tries to load the application on the root X, but it does not exist, while when you do sudo kcontrol it loads it in your own X :)

---

