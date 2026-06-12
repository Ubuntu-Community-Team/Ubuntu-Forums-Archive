---
title: "Help with multiple desktops."
date: 2010-07-27
forum: Desktop Environments
---

### Post by jules321 on 2010-07-27
Hi! I've been trying to configure multiple desktops in ubuntu 10.04. After failing miserably during 2 days, i got it somewhat working...

I own two monitors. The first one is an AOC F22 and the second one is a Dell 2007WFP, both wide format. The Dell monitor is able to turn to get in a vertical position, so my idea is to have the AOC as always (horizontal, i mean) on my left and the Dell on my right, but flipped (vertical). I decided to have different desktops in each instead of extending one.

I have it all working, except that, when i turn on the PC, the Dell monitor does not work properly. Instead, it shows a lot of funny colors. It seems to be the wallpaper but totally ripped off, distortioned. At this point, i'm able to move the mouse cursor to that screen and, strangely, it doesn't get distortioned.

I found a little hack to make it work as it should. I have to turn on the pc, log in, then open a terminal in the Dell monitor (terminal that i can't see, so i have to type blindly) and use the commands:

xrandr --output DFP4 --rotate normal <--- Now the image clears but the screen is not in the right position (it's horizontal)

and then

xrandr --output DFP4 --rotate left <--- This is the final position since the Dell monitor is in a vertical position.

I'm forced to use the "rotate normal" command first because if i do not, then the "rotate left" one does nothing. I suspect that the screen is supposedly already rotated to the left when i turn on the pc, but for some reason ubuntu doesn't like it.

I thought of using the commands as a startup application, but it didn't work. Since the two screens are independent, if i run the commands in the AOC monitor, they do nothing, but if i run them in the Dell monitor, they work like a charm. So i think that the problem with this method is that the commands are not running in the appropriate screen.

SO. The question is... How can i make a startup script with those commands but "selecting" the screen in wich they are ran? Somebody has other ideas?

Thanks in advance and sorry for the bad english!

---

### Post by jules321 on 2010-07-28
up.

---

### Post by jules321 on 2010-07-28
Auto-solved.

Today some updates appeared in the update manager. I installed them, and then all that i have got was gone. I had to reinstall the ati drivers (catalyst 10.6) and, for my surprise, when i tried to get the same config that i had before, strangely the Dell monitor started flipped with no distortioned :D. I don't know what did i update, but... it worked... 

Thanks anyway!

---

