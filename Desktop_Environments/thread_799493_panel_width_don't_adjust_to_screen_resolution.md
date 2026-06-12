---
title: "panel width don't adjust to screen resolution"
date: 2008-05-19
forum: Desktop Environments
---

### Post by RikoW on 2008-05-19
Hi all,

I recently upgraded my Dapper LTS installation to the latest Hardy LTS. Unfortunately, I have to say, that was the upgrade with the most problems so far I experienced with Ubuntu.

Anyway, I'm almost there. What still bugs though is that the panel width does not scale properly with the screen resolution. I'm running on Dell D600 laptop with and without docking station with an ATI Radeon Mobility graphics chip (xorg driver RV250). The build-in LCD has a resolution of 1024x768, the external LCD on the dock 1280x1024.

The top panel is stuck on 1024 width, no matter whether I'm running on the big or the regular screen. The bottom panel on the other hand, easily scales from 1024 to 1280 after clicking on it to move. It then just snaps in the correct position and extend over the entire screen width.

However, when I switch from the big screen to the smaller one, the bottom panel stays on the 1280 width, so that 1/3 of the panel on the left hand side is invisible.

Any ideas, how that could be fixed? BTW, in dapper there was no just problem.

Thanks and cheers,

                  Riko

---

### Post by bmac on 2008-05-19
Had a similar problem and found:
Config editor/apps/panel/default setup/toplevels
My top panel had "expand" checked. However, my bottom panel did not.
I simply checked the expand box in my bottom panel and the problem was resolved.


Hope this helps....

---

### Post by RikoW on 2008-05-20
No, didn't help :( both panels are set-up exactly the same way, except for the positions of course ...

Thanks though,

            Riko

---

### Post by Wandering on 2008-05-20
Have you tried deleting the panel and then making a new one. It can all be done in the gui.  You can right click the panel, and in properties check or uncheck expand. You can remove the panel or put in a new one, and place it where you want it. You can have lots of panels, and put pretty much what you want on any of them.

Good luck.

---

### Post by RikoW on 2008-05-20
been there, done that! no change! :(

---

### Post by Donalb on 2008-05-20
I don't like "me toos" but this is very similar to my situation. I'm also using a D600 with a docking station. Undocked everything is fine, the lappy screen res displays at 1024 x 768 fine, and will also do 1400 x 1050
However when docked I have a 19" generic LCD, and use 1024 resolution except.......the size is slightly off, i.e. the menu bar disappears off the bottom and I'm missing a smidge off the right hand side. Screen adjustment on the monitor doesn't work. 
I tried a PCLinuxOS Live CD (to have a look) and it displayed my monitor just fine.
Donal

---

### Post by RikoW on 2008-05-23
Seems like, even though I'm connected to the external LCD, the built-in one is sort of "running" as well. And with it's smaller resolution determines the maximum width of (some) applications - notably the to panel and the unity mode in VMware workstation 6.5b. Both screen seem to overlap. I tried to fix that under Preferences -> Screen Resolution.

However, when I start grandr (repos) and turn the internal screen off, the full screen is used. 

And don't worry, when you boot the laptop outside the docking station, it will use the correct, smaller resolution :)
But, if after that, you boot again in the docking station, you have to fire up grandr once more to turn the internal LCD off again.

There must be a better way to do that (without the need to turn the LCD off), but I haven't figured it out yet. I bet it's related to the fact, that my login screen is still restricted to the smaller resolution, even though the laptop sits in the docking station. None of the post I read so far helped. Did I mention, in Dapper I didn't have to do any mumbo-jumbo like this? :)

Anyway, this is a workable solution ....

Cheers,

              Riko

---

