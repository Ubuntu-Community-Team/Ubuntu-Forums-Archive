---
title: "want to prevent entering a password"
date: 2005-03-12
forum: Desktop Environments
---

### Post by lorap on 2005-03-12
each time i close display on my notebook,screensaver asks me to enter the password.
can i prevent it?
the option in the screensaver's configuration called "lock the screen" is disabled.
thanks.
pavel

---

### Post by oVerCaffeinated on 2005-03-12
Why would you want to prevent it? If you leave your laptop alone you don't want just anyone coming up to it and accessing it. It can't be too much trouble hitting in the password everytime the screensaver comes up. Unticking "lock screen" should work, if it doesn't, maybe just try putting 999999 in the minutes box.

---

### Post by lorap on 2005-03-12
hi friend!
as i've written above the option "lock the screen" is disabled.
but anyway thanks for attention!
thanks
pavel

p.s.:
i don't really need this option cause i've nothing to hide :-)
neither from my wife nor from the students i study together.

---

### Post by dave9191 on 2005-03-12
Hey, Ive not tried this, so dont blame me if something goes wrong :)

But when you close the lid, a shell script is executed that forces the screen lock option. Thats why turning it off in the settings makes no difference. The script that is executed is /etc/acpi/lid.sh .

I had a quick look for you how it works, and from what i can see it calls another file when you close the lid. 
/usr/share/acpi-support/screenblank. 

In that file you should see the following line 
su $user -c "(xscreensaver-command -throttle && xscreensaver-command -lock)"

if you change this to be 
su $user -c "xscreensaver-command -throttle"

it should (in theory) stop the locking of the screen when you close the lid. The screen should still turn off when you close it. 

Hope it works, 
Dave

---

### Post by lorap on 2005-03-13
Dave, thank you very much!
i'll try it once i get home(i'm at institute right now).
thank you very much for the time you've spent to help me solve the problem.
pavel

---

### Post by dave9191 on 2005-03-13
Hey no probs, we all have to help each other :) Tell me if it worked.

---

### Post by jakes on 2005-04-12
For anyone, that stumbles across this thread and wonders if the instructions given above do in fact disable the screen locking when you close your laptop lid, they do.
This is the only way I've found that will stop this happening. Thanks for your tip dave9191.
Cheers,
jakes,

---

