---
title: "Ubuntu having problems with video drivers?"
date: 2009-04-13
forum: General Help
---

### Post by Taj1993 on 2009-04-13
Hello, 

About 3 days ago I switched to Ubuntu and it's rather remarkable. I am a complete novice to Linux in general however. But im pretty decent with Windows Programming and such. But I've been having an odd problem recently.

I have two versions of Linux as shown below

[IMG]http://i30.photobucket.com/albums/c308/legendeath/OS.jpg?t=1239646052[/IMG]

11 and 7, I do not know the differences between the two.

When I first booted up everything seemed ok and fine. I was installing things fine. I had installed the Nvidia 180 Driver. But after my third boot or so it started to boot up into a text mode that displayed a screen like so.

[IMG]http://i30.photobucket.com/albums/c308/legendeath/ErrorMessage.jpg[/IMG]

I would first get it on Ubuntu 11 so I decided to boot on Ubuntu 7 but after a couple boots on Ubuntu 7 It also appeared. I did memory checks and recovery mode for both of these. But it did nothing I evnetually did a StartX on it and got something like this.

[IMG]http://i30.photobucket.com/albums/c308/legendeath/StartX.jpg[/IMG]


What's odd is that once or twice I didn't receive the message shown and I would boot regularly. Which leads me to ask what is wrong with my Ubuntu. I'm guessing it's because I have a restricted driver? I have tried searching for the answer but to no solution. Im guessing it's also not just the 180 driver as I tried going back down but it still was showing up with all that.

---

### Post by SunnyRabbiera on 2009-04-13
Well the reason why you see two Ubuntu's is because of updating, usually for safety reasons the older kernel is listed just in case the newer one doesn't work.
Video drivers can break with kernel updates, but hopefully a more experienced user in that area can help you as I dont use a nvidia/ATI card therefore not needing to use special drivers.

---

### Post by Taj1993 on 2009-04-15
Update: 

I've tried just completely reinstalling Ubuntu and yet I still get this error. My drivers are now down to Nvidia 177 Im guessing I should try to alter Xorg.conf file? Im guessing it's completly plausible that Compiz could have a role in this?

Oh, and im using SLI 9800 GTX+.

---

