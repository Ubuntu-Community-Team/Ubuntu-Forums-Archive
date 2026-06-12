---
title: "rotated desktop, now it won't work"
date: 2009-01-17
forum: General Help
---

### Post by duhglas on 2009-01-17
Hey I just set up ubuntu on a new computer, and havign trouble getting everything working right. I was messing around, and decided to rotate the whole screen left, and now it's stuck in there, and I am unable to access or do anything in ubuntu. Mouse still moves, but it's jsut a blank yellow screen now. No clue what to do now.

---

### Post by duhglas on 2009-01-17
Hey, I really need some ideas here. Unbuntu isn't working at all for me, so i need to gte this figured out. In case people didn't understand what i meant, i in the in one of the screen options area i decided to change the screen and rotate it left, and now it's completetly screwed up, and i can't change the option back. Not sure what to do any ideas greats appreciated, as I am a ubuntu noob. Thx

---

### Post by metallicamike on 2009-01-17
did u try restarting?

---

### Post by duhglas on 2009-01-17
yep restarting did nothing

---

### Post by metallicamike on 2009-01-17
hmm, does the login screen show up?

---

### Post by duhglas on 2009-01-17
yep, it shows up normally, upwards, i sign in then it messes up.
I was thinking, not sure what it's called, but like the ms-dos thing, for ubuntu, is it called gnome, not sure if u know what i mean, but where u type commands in. Trying to get to that and typing in the command to change that setting if we can figure that out.

---

### Post by lakersforce on 2009-01-17
Boot up in "recovery mode" and choose "restore X" (or something simmilar).

If that does not work, re-install. And may I suggest that you create a seperate partition for your /home...?

---

### Post by Rhubarb on 2009-01-17
If you are able to open up a terminal, or are able to press Alt + F2, enter this in:

```
xrandr -o normal
```

Run the above and your display's orientation will be set back to normal (from being rotated left / right / upside-down).

---

### Post by theozzlives on 2009-01-17
If you do re-install, boot with the live CD and backup your data!!

---

### Post by duhglas on 2009-01-17
Ok good i got it working using the alt + f2 xran... method. However it is a little glitchy, I restart my system, and that helped somewhat but still some the power icon that is normally in top right is now in top middle of the screen adn the recycle bin icon is moved as well, and the the rigth edge, about an inch of the actual monitor, the ubuntu system doesn't cover and is just black. Not sure why it's done this, or how to fix it. I checked my monitor resolution and it's same as before, 1680X1050, which is monitor's native resolution, so not sure what to do.

---

### Post by Rhubarb on 2009-01-17
> **duhglas said:**
> Ok good i got it working using the alt + f2 xran... method. However it is a little glitchy, I restart my system, and that helped somewhat but still some the power icon that is normally in top right is now in top middle of the screen adn the recycle bin icon is moved as well, and the the rigth edge, about an inch of the actual monitor, the ubuntu system doesn't cover and is just black. Not sure why it's done this, or how to fix it. I checked my monitor resolution and it's same as before, 1680X1050, which is monitor's native resolution, so not sure what to do.
You should be able to right click on the power icon / recycling bin icon, uncheck "Lock to Panel" if it is checked, then right click on the icon again, and select "Move".
Then you may move the icon to where ever you want to put it.

---

