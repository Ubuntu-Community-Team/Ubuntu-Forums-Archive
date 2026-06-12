---
title: "Random freezes with compiz fusion on gutsy"
date: 2007-12-02
forum: Desktop Effects &amp; Customization
---

### Post by Spitz on 2007-12-02
Hi, I have a Dell 1405e/640m laptop with a integrated Intel 945GMA graphics card.

My system tends to have random freezes where the screen and keyboard do not work. The mouse however moves nicely about, and the only keyboard commands that work are SysRq commands. The Alt+PrintScreen+k is able to kill X, but it isn't able to restore it again, and therefore the only thing I can do is rebooting by using the powerbutton or Alt+PrintScreen+b.

It looks like it is more likely to freeze when using memory heavy programs, like OOo (esspecially when scrolling) and sometimes Firefox, but it also happens when only running smaller programs.

I would be really happy if someone found a solution to the problem, since I love all the compiz fusion effects and it is a drawback to turn compiz of every time I am doing something important on my computer.

---

### Post by jonray74 on 2007-12-05
Hello,

I too have experienced a lockup, freeze, and my screen goes blank unconditionally at random times after I enabled the Restricted drivers for my ATI 9600 Pro Radeon card, and installed the XGL server and Compiz-Fusion.

When I start to play my DVDs using Totem xine, the screen goes blank, and I press CTRL+ALT+Backspace to reboot cause i couldn't get the screen back. Other times is when i'm running apps, (ie firefox, or OpenOffice, etc.) that the screen freezes but i can move my mouse but can't click on any icons. 

I also experience complete freeze when i'm downloading for instance or just opening Synaptic or any apps or just simply moving my windows. Really odd.

Prior to enabling the Restricted drivers, the system ran perfectly without lock-ups and I could play around with Compiz-Fusion with cubes, play DVDs, run multi-apps with the exception of screensaver being off cause the ScreenSaver just runs very slow with the standard drivers, other than that, I can do whatever with it but the disadvantage of just using the standard drivers not the proprietary ATI drivers. After I enabled the Restricted drivers, and installing XGL (i've tested this 20x now after so many re-installs), that's when I get the lock-ups, freezes. Somehow i'm finding now, that the culprit maybe in the enabling of the Restricted drivers and installing XGL and running Compiz-Fusion with it, at least for me, after doing 20x of re-installations.

So my conclusion to this is for now is, to use the standard drivers that came with Ubuntu and not the proprietary drivers. I don't know as to when these proprietary drivers will be able to support all types of ATI cards, but as of now I will try not to get into the temptation of re-enabling the Restricted drivers because I know for sure, that the system will start locking up, once they've been enabled. Having reinstalled my Gutsy 20x now enabling and disabling the Restricted Drivers.

Anyways, that's my thoughts on it. If anyone experienced the same, stick with the default installation of Ubuntu for now, since Compiz-Fusion runs well on it. At lease for me it did after I re-installed Gutsy, the only disadvantage is that I couldn't get my Video Card to run to its full capacity (ie, do full 3D rendering, enabling 3D Screensavers) because it's using the default drivers supplied by Ubuntu.

:)

---

### Post by Spitz on 2007-12-09
Hi, thanks for the answer, but my Intel Graphics card does not have a need for any non-free drivers.  It is (I believe) fully supported by the intel-xserver. Also the problem seams to occur on both Intel, ATI and Nvidia card, so I would suppose the issue does not have anything to do with specific drivers and graphic cards.

---

