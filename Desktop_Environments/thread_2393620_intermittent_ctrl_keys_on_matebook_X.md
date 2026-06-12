---
title: "intermittent ctrl keys on matebook X"
date: 2018-06-05
forum: Desktop Environments
---

### Post by yuzuuser on 2018-06-05
Just installed xubuntu 18.04 on a huawei matebook X with a japanese keyboard.
After the initial install everything looked great, but after powering on the next day i noticed that the control keys weren't working (do not show up in xev or showkey) ... funny, i'm sure they worked last night...
There's a lot of "control key not working" forum content to get through (mostly keyboard shortcut related), but none of it worked for me (gnome-tweak-tool included). Apologies if i somehow missed the killer thread.

After scratching my head a few hours i noticed that they started showing flickers of life ... working intermittently ... few hours more, the battey is running down so i connect the power - then they're suddely working 100%. 

Have now repeated several times and as far as i can see it's like this:
[LIST]
[*]from power on with battery only : ctrl keys not working 
[*]on battery, after a little use (crazy ctrl-c'ing in terminal window) : start working intermittently, but not to a useable degree 
[*]with power connected : work 100% 
[*]behaviour is exactly the same for L/R ctrl keys. No other keys have problems 
[/LIST]

Unfortunately this was a new laptop and i deleted windows so i have no evidence that it's not a h/w fault, but i don't see how a hardware fault would affect **only, and both** ctrl keys.

Any ideas?
:confused::confused:

---

### Post by VMC on 2018-06-06
"Settings > Hardware > Keyboard"
What does your keyboard layout show?

---

### Post by yuzuuser on 2018-06-07
Thanks for responding.
Currently it is set to Japanese (kana 86), the model, customization and compose key options are all unset (menus show "-").
I have tried a couple of the other japanese layouts too but didn't notice any difference in behaviour. To be honest i don't know what the most correct setting is here.

**UPDATE: **kana-86 *is *the correct setting, but this is irrelevant to the problem.

---

### Post by yuzuuser on 2018-06-17
... after that, i accepted some auto-updates, and then the ctrl keys stopped working alltogether ... have now given up and arrived at a useable environment via a bunch of xmodmaps.

I guess this is a matebook issue, rather than any shortcut/keyboard mapping thing (as discussed elsewhere, media keys also don't work on matebook linux). Would still be interested to hear from anyone who has a properly working matebook X with JP keyboard, or who has seen this seemingly power-related intermittent behaviour.

---

