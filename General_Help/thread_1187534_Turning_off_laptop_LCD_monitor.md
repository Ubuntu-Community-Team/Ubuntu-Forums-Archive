---
title: "Turning off laptop LCD monitor"
date: 2009-06-14
forum: General Help
---

### Post by oakdeveloper on 2009-06-14
Hi,

I am having a Dell Studio 15 running Jaunty. I would like to know how I could turn off my LCD monitor completely with the system still running. I want to use the laptop to play music. So during that time I don't want to waste power by keeping the monitor on. I have tried setting the screen saver to blank screen but still there is some light in the monitor and it does not get turned off. Please help me..

Regards,
Babu

---

### Post by kevinlyfellow on 2009-06-14
If you type in the terminal
```
xset dpms force off
```

I suggest you make a button on a panel by 
1. right clicking on the panel
2. choose add to panel
3. create custom application launcer
4. Name it whatever you want
5. in command put in xset dpms force off
6. This works great with touchpads, terrible with mice

---

### Post by oakdeveloper on 2009-06-15
Thanks Kevin! But it doesn't seem to work for me. I've tried the command as suggested by you. The monitor is not getting turned off completely. There is still some backlight in the monitor. Any other suggestions to make it work ??

---

### Post by malachi1990 on 2009-06-15
Just out of curiosity, what does simply closing the lid do, and what options in the power management GUI have you tried? (System -> Preferences-> Power Management)

---

### Post by oakdeveloper on 2009-06-15
In Power Management, I've chosen "Blank Screen" for the action to be taken when the lid is closed. The backlight in the monitor is still on when I close the lid as I can see it through the small slit between the lid and the base of the laptop. I have not tried other options like Suspend or Hibernate as I want only the monitor to be turned off and not the running processes in the system.

---

### Post by greenie9 on 2009-06-15
i have the same issue as you :)
just out of curiosity, do your brightness buttons work?

---

### Post by abn91c on 2009-06-15
why do you just use the Fn+f3/f5/f1 key combination to turn off ldc that way?

---

### Post by wpshooter on 2009-06-15
I am not sure that it works the same way on a laptop that it does on a desktop but if it does have you tried setting the "put display to sleep when inactive for" parameter under System/Preferences/Power Management AC Power & UPS Power tabs to something other than NEVER ?

P.S. - Mine goes completely blank/black as the ace of spades.

       As Woody Woodpecker said when the doctor asked him what it was that he saw when he looked into the bowl of vegetable soup: "I CAN NOT SEE A THING".

       Dang, let me set that back to never, that black screen coming on is sort of unnerving.

---

### Post by oakdeveloper on 2009-06-16
> **greenie9 said:**
> i have the same issue as you :)
just out of curiosity, do your brightness buttons work?

I have tried setting the brightness through System --> Preferences --> Power Management. But it doesn't work for me.

---

### Post by oakdeveloper on 2009-06-16
> **abn91c said:**
> why do you just use the Fn+f3/f5/f1 key combination to turn off ldc that way?

I did Fn+F1. But it turns off my CPU too. My system goes to sleep state. Fn+F3 gives some information about Power and battery. Fn+F5 has no effect.

---

### Post by oakdeveloper on 2009-06-16
> **wpshooter said:**
> I am not sure that it works the same way on a laptop that it does on a desktop but if it does have you tried setting the "put display to sleep when inactive for" parameter under System/Preferences/Power Management AC Power & UPS Power tabs to something other than NEVER ?

P.S. - Mine goes completely blank/black as the ace of spades.

       As Woody Woodpecker said when the doctor asked him what it was that he saw when he looked into the bowl of vegetable soup: "I CAN NOT SEE A THING".

       Dang, let me set that back to never, that black screen coming on is sort of unnerving.
The least value which I could set for the parameter "Put display to sleep when inactive for" was 6 minutes. But even after 6 minutes of being idle, the display doesn't turn off. The screen goes blank though but there is still some lighting.

---

### Post by greenie9 on 2009-06-16
> **oakdeveloper said:**
> I have tried setting the brightness through System --> Preferences --> Power Management. But it doesn't work for me.

same issue here =)
(see my thread in signature)

---

### Post by greenie9 on 2009-06-16
ok, there is definitely something funky going on here...
along with my brightness keys, the eject button on my laptop works for a little while then stops...

both seem to be tied together

---

### Post by greenie9 on 2009-06-16
ok, i think the brightness up/down keys is something a little more serious
Went to put a disc in my computer, then pressed the eject button on my keyboard, and, well, it didnt work

a restart later, and it is all working fine (as are brightness keys) then, eventually the eject button stops working, as do the brightness keys

i am not sure of the process/file/whatever it is that controls keyboard inputs, but i have a feeling that that is where the problem lies (although the volume keys work fine)

---

### Post by wpshooter on 2009-06-16
> **oakdeveloper said:**
> I have tried setting the brightness through System --> Preferences --> Power Management. But it doesn't work for me.

Have you tried setting "put display to sleep when inactive for" to lowest possible setting and setting "set display brightness to" lowest available percentage and then unchecked the "Dim display when idle" box.

---

### Post by greenie9 on 2009-06-16
Well, i have the backlit keyboard if that makes any difference at all...

also, went to install windows in a VM, realised i had put in wrong disk, went to press the eject button, and nothing happened

right clicking on the disk on desktop and hitting eject worked
so, i rebooted, and the eject button (and brightness keys) worked fine

eventually the brightness keys stopped working again, and once i noticed this, i tried the eject button, which didnt work either

In keyboard shortcuts i assigned ctrl+alt+E to eject, and it worked straight away

it appears to me that it is something to do with keyboard inputs, i tried all the different keyboard configs, none of them sorted out my issue(s)

i dont know enough about how ubuntu/linux work with keyboard shortcut recognition, but it appears that the process dies at some stage after log in (no difference between opening no programs, and opening everything i can)

---

### Post by kevinlyfellow on 2009-06-18
Here's a thread related to the issue, perhaps there is something in it that can be used

[http://ubuntuforums.org/showthread.php?t=297316](http://ubuntuforums.org/showthread.php?t=297316)

---

### Post by oakdeveloper on 2009-06-19
> **wpshooter said:**
> Have you tried setting "put display to sleep when inactive for" to lowest possible setting and setting "set display brightness to" lowest available percentage and then unchecked the "Dim display when idle" box.

I have tried this too. But it doesn't work. The backlight is still on.

---

### Post by oakdeveloper on 2009-06-20
Finally, I have found the solution [here]("http://oesediez.blogspot.com/2007/12/adventures-in-ubuntu-land-turn-off.html"). It works perfectly.

---

