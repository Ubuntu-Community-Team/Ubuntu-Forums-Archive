---
title: "Linux Screen Resolution, Part 2"
date: 2008-10-07
forum: Desktop Environments
---

### Post by c.pergiel on 2008-10-07
I finally returned to the [screen resolution problem]("http://pergelator.blogspot.com/2008/09/horrible-harry-linux-screen-resolution.html") on my Linux box today. I was able to boost the resolution up to the max of 1600 x 1200, which is so good that this text I am writing is almost too small to be legible. I did this by adding three lines to the "Screen" Section of [/etc/X11/xorg.conf]("http://docs.google.com/Doc?id=dgz3q3nn_197fscj6ggg"):

    SubSection "Display"
    Modes "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection

All is still not right however. CTRL-ALT-"Keyboard Minus Key" and CTRL-ALT-"Keyboard Plus Key" will cycle through these six available resolutions, but the menu bar at the top of the screen is only available on the first one (1600x1200). I should be able to get the resolution I want by editing this file and putting the resolution I want at the head of the list. We shall see.

System/Preferences/Screen Resolution has it's own set of problems. Clicking on the Resolution box gives you a much larger drop down list now, but it still has the big white space above the highest resolution. That's minor. What's bad in my case is that the list of resolutions is extensive, it includes many that are NOT in the list in xorg.conf. This is a problem because resolutions that are not in the list DO NOT WORK with my monitor. Selecting one of these other resolutions cause the monitor to simply shut down.

---

