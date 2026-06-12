---
title: "HDMI out to LCD Display Issues"
date: 2009-04-14
forum: General Help
---

### Post by x C0MMAND0 x on 2009-04-14
Alright,

So I have been trying to fix this for about a week now on my own and done a LOT of research, and messed with the NVIDIA X SERVER SETTINGS, and messed with the /etc/X11/xorg.conf file.  I can not get this set up properly.

Here is what I want to be able to do: Use the HDMI output from my laptop to connect to my TV and have the display look correct on my TV. Ideally, I would be able to have the display on my laptop AND on my TV at the same time, in their corresponding resolutions, but if I could just get it to look proper on my TV I would be happy.

I have a Dell XPS M1330 which runs at 1280x800.
I have a Panasonic TV which runs at 1280x720.

I can get the image on both at the same time, but on the TV there is a "scrolling" issue; the entire screen is not displayed all at once I have to move the mouse to the top or bottom of the screen in order to see the rest of my desktop.  I can not figure out how to get this display to work correctly, and I know that it is an issue but I can NOT find a solution.

I heard that using "Option         "TVOverScan" "0.0"" can fix the issue but I have not had luck.  Perhaps someone could help me with an xorg.conf file properly setup for this?

---

### Post by x C0MMAND0 x on 2009-04-16
Please help.  I can't be the only one who has this problem...

---

### Post by x C0MMAND0 x on 2009-05-01
Help.  Is this solved in Jaunty?

---

### Post by x C0MMAND0 x on 2009-07-20
I still have had no luck with this issue.  Does anybody know how to get the HDMI out resolution to be proper on my TV?

---

### Post by xoom on 2009-08-06
The only solution I have found is to disable the LCD on my m1330. At that point the resolution on the external screen (1280x720 projector in my case) is correct with no overscan.

I have tried geting Seperate X screens to work but haven't had any luck with that either.

I guess it's not much of a solution for you but more of just a bandaid for now.

---

