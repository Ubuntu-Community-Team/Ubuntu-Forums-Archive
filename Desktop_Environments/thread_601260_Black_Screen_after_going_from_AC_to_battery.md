---
title: "Black Screen after going from AC to battery"
date: 2007-11-03
forum: Desktop Environments
---

### Post by nefhyg on 2007-11-03
Hello.

I just upgraded my feisty distribution :mad: to 7.10. Then something very strange is happening:

it goes like this...

1 - my notebook is on running on AC.
2 - I don't turn it off, just disconnect from the AC, and use the battery power. As soon as I disconnect from the AC, my LCD screen goes black! (notice that it was supposed to lower to 70% only, and it happened just fine on feisty). If I go back to the AC, the screen lights up again.

Any suggestions, it's some new bug on gutsy.

Thanks.

---

### Post by nefhyg on 2007-11-03
I tried this... I installed kpowersaved. Then if I try to alter the lcd's brightness when going from AC to battery the screen goes BLACK! It doesn't matter if I move from 100% to 99%. The screen goes black.

It worked perfectly on feisty, so it's something new, any suggestions or is someone having the same problem?

I can give details of my notebook as needed.

It's real bad when I can't disconnect from AC without getting a black screen...

Thanks.


> **nefhyg said:**
> Hello.

I just upgraded my feisty distribution :mad: to 7.10. Then something very strange is happening:

it goes like this...

1 - my notebook is on running on AC.
2 - I don't turn it off, just disconnect from the AC, and use the battery power. As soon as I disconnect from the AC, my LCD screen goes black! (notice that it was supposed to lower to 70% only, and it happened just fine on feisty). If I go back to the AC, the screen lights up again.

Any suggestions, it's some new bug on gutsy.

Thanks.

---

### Post by archivalbackup on 2007-12-03
Ka Bump!

I have this exact same issue on a Gateway Tablet TA6. I found that I could restore the backlight for a few seconds by using the built in brightness controls (Fn+F1, FN up/down). The backlight goes off after a few seconds again and basically make my computer unusable on batter power. 

I dont get any entries in dmesg when I switch from AC to battery. 

I also changed my power management to do nothing when on battery, lid closed, inactive etc. I put Dim Brightness at 100% and dim when inactive unchecked. 

Help?!

---

### Post by bdcheung on 2007-12-03
I also experience this on my Sager 6630, but find that pressing any key will resolve the screen back to normal brightness.

---

### Post by LiGy on 2008-01-14
I'm getting this too on a Dell 700m.

Some further experimentation reveals that switching from ac to battery power triggers whatever action is tied to the lid button on battery power-- i.e. if the lid close event is set to suspend, then it will suspend when one switches to battery power. 
Though, even more interesting, this behaviour does not occur consistently. At some point near the end of the charge cycle, this behaviour stops, but before that point, it will constantly occur, and seems to coincide with the "Action Forbidden: Policy Timeout" messages. Further testing is needed on this last point though.

Perplexing, certainly.

---

### Post by DrMeers on 2008-06-20
Same problem here on 8.04, BenQ Joybook S61
Seems to occur if I unplug the power just as the screensaver is about to activate -- I pull the plug, and the 'fade-to-black' transition occurs, but then nothing brings back the display apart from:
[LIST]
[*]<Ctrl><Alt><Backspace> (restart X -- ugly)
[*]Close laptop lid (Hibernate -- restores session OK on reboot)
[/LIST]

I imagine it is to do with the fact that there are different power management rules regarding turning display off, etc depending on the power source, and the system is getting into a strange state if the power source changes at an inopportune moment?

---

