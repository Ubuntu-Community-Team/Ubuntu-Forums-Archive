---
title: "Installation problem, live CD freezes after booting!"
date: 2007-03-10
forum: Desktop Environments
---

### Post by Spiros- on 2007-03-10
Hello people, I'm having a problem with the Ubuntu 6.10 Live/Installation CD. First of all, please excuse me for my poor English, you see it's not my mother tongue.

I downloaded Ubuntu 6.10 live CD and decided to burn it into blank media to install it on my system. I also disconnected all my HDDs and only left one; the installation's target disk. I had some problems with previous releases with the boot manager installing in the wrong physical disk, so that's why I did that. Everything is perfect till that stage, I select my language from the boot menu [F2] and proceed. Ubuntu loads, with the progress bar showing that, but after some time it completely freezes (I also see some graphics artifacts on my screen after the "crash").

What's going on? I tried using safe graphics mode to boot with the very same result. I also checked the media with the "Check CD for defects" option and it's absolutely OK. I also changed the boot parameters, removing the "silent" part so that I could see what's going on. From the X debug report I see that it cannot find a.. monitor (says: "No screens found")?!

Can you please help me with this? Or I'll just have to stick with my 6.06 installation? :(

---

### Post by jksigurd on 2007-03-11
I'm basically having the same exact problem.  For me, right after the progress bar loads, it goes to a blank beige background with a cursor, but then the installation hangs there with some graphic artifacts in the middle of the screen.  Although I did get through the first loading screen, the progress bar there was glitchy looking with artifacts too. 

I *think* the next step is for it to ask for my language, but it never gets that far.

Any help on this would be greatly appreciated.

---

### Post by jksigurd on 2007-03-11
I found out the problem I was having was due to my Nvidia 7800GT graphics card being incompatible with the Nvidia driver on the installation CD. I found a workaround in this post:

[http://ubuntuforums.org/showthread.php?p=2268952](http://ubuntuforums.org/showthread.php?p=2268952)

Even if you don't have the same card it might be worth trying.

---

### Post by Spiros- on 2007-03-11
I know there are issues with certain graphics processors. I had these issues with the 6.06 version as well, but booting with safe graphics more would do the job.

And no, I'm not using the 7800GT GPU. I'm having an ASUS ATI Radeon X850 Pro.

---

### Post by Spiros- on 2007-03-13
OK, even if I didn't get an answer, I managed to find out what I should have done, thanks to **aberry5555** and a [ [recent post]("http://ubuntuforums.org/showpost.php?p=2193083") ] of his.

---

