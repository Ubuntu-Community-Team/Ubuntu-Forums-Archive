---
title: "Is there any way to restore auto-hide launcher on Maximized windows in Unity?"
date: 2014-07-10
forum: Desktop Environments
---

### Post by jusko on 2014-07-10
Hello :-)

I'm not much user of Ubuntu so i'm not an expert (i've used Ubuntu few years but in old-days of classic Ubuntu up to 8.04), Fedora with GNOME3 is my primary distro from years :)

Driven by sentiment i've installed Ubuntu 14.04 two days ago. I've used Ubuntu 11.10 and 12.04 in my work and was nice - good visuals, Radiance + nice wallpaper and it's have nice looking.

But my problem is - when i've used Ubuntu in work i remeber that Unity had native feature to auto-hide launcher on maximized windows (ex. on maximized web-browsers). It was nice feature, i've like it, but it missed on modern Unity ;) 

Is there any way to restore this? I know, i may set normal auto-hide but dragging launcher back every time by mouse is tiring - that old trick was better for me, hiding only on maximized windows. 

The reason is that there is one bar (status bar) on the top and one on the left (launcher) - because of this i have feeling that everything is tightly packed and my laptop monitor is smaller than it really is (15,6") :)

I've tried old method like: [http://www.webupd8.org/2013/02/how-to-get-unity-launcher-window-dodge.html](http://www.webupd8.org/2013/02/how-to-get-unity-launcher-window-dodge.html) but it won't work.

   I appreciate your help :)

Best regards :)

---

### Post by mc4man on 2014-07-10
> I've tried old method like: [http://www.webupd8.org/2013/02/how-t...dow-dodge.html](http://www.webupd8.org/2013/02/how-t...dow-dodge.html) but it won't work.
I don't see why it wouldn't work in 14.04 to the extent it did in 13.04 (raring
Just grab the .deb & install with software-center or install wmctrl then install the .deb with dpkg -i /path/to/unity-dodge-maximized-windows_1.6.1-1~webupd8~qr~2_all.deb

[https://launchpad.net/~nilarimogard/+archive/webupd8/+files/unity-dodge-maximized-windows_1.6.1-1%7Ewebupd8%7Eqr%7E2_all.deb](https://launchpad.net/~nilarimogard/+archive/webupd8/+files/unity-dodge-maximized-windows_1.6.1-1%7Ewebupd8%7Eqr%7E2_all.deb)

Log out/in & see if it suits & or causes issue

---

### Post by jusko on 2014-07-11
Thank You for reply.

I've installed this deb before. For me - it set laucher auto-hide both for maximized windows or not, just normal, native launcher auto-hide and i had problems with turn auto-hide off in Unity Tweak Tool (even if i've set auto-hide to off, it's still hide). So - maybe it worked in previous versions of Unity, but not anymore. 

To turn-off launcher auto-hide i've had to uninstall this deb - then everything back to normal.

Man - it was native option, why they removed it :-/ Sometimes Canonical decisions are not logic to me, because you never know what's waiting in new release :-(

Maybe i'll try once again - maybe last time something went wrong.

---

### Post by mc4man on 2014-07-11
I gave it a try, works as expected in 14.04
It has nothing to do with unity settings & or the tweak tool. Here I have autohide off in unity (the default


what the .deb does is install a script to /usr/bin & an autostart .desktop to /etc/xdg/autostart/
It can be turned on or off in 'Startup Applications' as seen in screen (disabled
Attached is a very short vid demonstrating

---

### Post by jusko on 2014-07-12
I've installed deb once again, typed unity-dodge-maximized-windows like in how-to etc, then rebooted Ubuntu just in case, but still nothing. Launcher won't hide, script is activated and is in autostart. I've recorded quick video, but i'm not familiar with recordmydesktop so video is a little too slow, but it can be seen that launcher not hiding - even if windows are maximized (it can be seen on attached image too). It's stock up-to-date Ubuntu 14.04.

I'm not newbie - i'm using Linux from 7 years but i don't have much experience with Unity so maybe i need to so something more than install deb and reboot the system?


Recorded video: [https://vid.me/S2U](https://vid.me/S2U)

---

### Post by mc4man on 2014-07-13
Log into a guest session & see if it works there..

---

