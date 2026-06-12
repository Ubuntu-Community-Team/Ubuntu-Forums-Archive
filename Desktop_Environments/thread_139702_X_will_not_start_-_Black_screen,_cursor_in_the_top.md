---
title: "X will not start - Black screen, cursor in the top left"
date: 2006-03-04
forum: Desktop Environments
---

### Post by Fallom on 2006-03-04
When X starts, I don't get an error. It just goes to a black screen with an underscore in the top left (_). I've tried going into recovery mode and doing dpkg-reconfigure xserver-xorg and selecting vesa mode, but that doesn't change anything. What's going on?

ATI Radeon X800
Nforce 4 Motherboard
AMD64 3000+

---

### Post by fuscia on 2006-03-04
i have no idea if you're in the same situation i have been at times, but my solution was to do ctrl+alt+backspace. are you using a display manager? i ran into trouble when i tried to do without one.

---

### Post by dcstar on 2006-03-04
[QUOTE=Fallom]When X starts, I don't get an error. It just goes to a black screen with an underscore in the top left (_). I've tried going into recovery mode and doing dpkg-reconfigure xserver-xorg and selecting vesa mode, but that doesn't change anything. What's going on?

ATI Radeon X800
Nforce 4 Motherboard
AMD64 3000+[/QUOTE]
Try selecting a low resolution (800x600) to see if it helps.

---

### Post by Fallom on 2006-03-04
I've been doing fresh installs of Ubuntu. On the first bootup X will crash because it's trying to load the ati driver, but when I switch it to vesa I get the black screen. I'll try setting it to 800x600.

---

### Post by Fallom on 2006-03-04
No dice. When I boot up it will start X and show the black screen with the character at the top left. The _ will flash a few times and then stay on the screen. No keyboard commands will work.

---

### Post by fuscia on 2006-03-04
did you do a default installation, or a server install?

---

### Post by redsox59 on 2006-03-04
I have the exact same issue. I just made a thread about this not seeing this post. I have an older pc which was able to run Ubuntu no problems, but my main machine has your same issue. I am frusturated and am looking for a solution because I want to have linux on my main one.

---

### Post by fuscia on 2006-03-04
did you guys try *sudo dpkg-reconfigure xserver-xorg*? 

edit: here's a 'how-to' about reconfiguring xorg. the above is included in it. [http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

---

