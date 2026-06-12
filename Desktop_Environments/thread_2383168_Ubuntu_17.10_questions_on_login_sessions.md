---
title: "Ubuntu 17.10 questions on login sessions"
date: 2018-01-21
forum: Desktop Environments
---

### Post by ubunt72 on 2018-01-21
I really tried to find the answers, searching the forum and then doing a google search.  

Sorry, I can't find it/them.

So, here goes - the questions here.

I checked this thread but it didn't fully answer my questions:
[https://ubuntuforums.org/showthread.php?t=2381588&highlight=wayland](https://ubuntuforums.org/showthread.php?t=2381588&highlight=wayland)

I know that 'Ubuntu on xorg' is the '"Ubuntu on Xorg" is like all the buntu's we have become accustom to."

But, what is 'Gnome on xorg' then?   My choices when I originally upgraded to 17.10:

Ubuntu on xorg
Gnome on xorg
Gnome Classic

I know that I don't have one that excludes 'xorg' because I am using a semi-recent nvidia card and was using the proprietary driver - apparently, that is not supporting (not compatible with?) Wayland.  I somewhat understand that.  

But, what's the differences between 'Ubuntu on xorg' and 'Gnome on xorg?'   Ubuntu switched to Gnome, I thought, so why is there separate sessions there?

I have one issue (btw) in which my application only works when I use 'Ubuntu on xorg' but that's a separate issue/topic, I guess.

I'm wondering what those differences are and why there's a separate session - is there some variation of Gnome and the xorg sessions?  I believe Gnome Classic is just the Gnome 3 desktop with some changes (including only certain gnome shell extensions installed?)?   

If I eventually use an open source Nvidia driver, will Wayland be available?  I decided to enable some ppa software that includes 'newer' versions of the nvidia drivers - and it lists newer versions that are 'open source' which is unexpected and odd.   If I upgrade or enable the use of those drivers, will they make the system compatible with Wayland?  For e.g., the currently installed driver is 384.x.   The new drivers now listed as available in the Software Updates (?) application include 387 and 390 which are listed as open source (Available Drivers).   Does anyone have any insight or info on those? 

Thanks for any help/info.

---

### Post by Frogs Hair on 2018-01-21
The Ubuntu on Xorg uses old display sever and the Ubuntu session uses Wayland which is still in development. Gnome Classic has a bottom panel and window list feature.


[https://en.wikipedia.org/wiki/X.Org_Server](https://en.wikipedia.org/wiki/X.Org_Server)

Wayland:

 [https://wayland.freedesktop.org](https://wayland.freedesktop.org)

---

### Post by ubunt72 on 2018-01-22
> **Frogs Hair said:**
> The Ubuntu on Xorg uses old display sever and the Ubuntu session uses Wayland which is still in development. Gnome Classic has a bottom panel and window list feature.


[https://en.wikipedia.org/wiki/X.Org_Server](https://en.wikipedia.org/wiki/X.Org_Server)

Wayland:

 [https://wayland.freedesktop.org](https://wayland.freedesktop.org)I knew all that.  What's the difference between Ubuntu on Xorg and Gnome on Xorg?

---

### Post by Frogs Hair on 2018-01-22
Gnome on Xorg does not appear on my 17.10 installation. Were you running the Gnome Shell prior to upgrade ? I see Ubuntu and Ubuntu on Xorg .

---

### Post by deadflowr on 2018-01-22
> **ubunt72 said:**
> I knew all that.  What's the difference between Ubuntu on Xorg and Gnome on Xorg?

Branding.
The Ubuntu version has Ubuntu theming(?) and branding embedded, where as gnome does not.

---

### Post by ubunt72 on 2018-01-22
> **Frogs Hair said:**
> Gnome on Xorg does not appear on my 17.10 installation. Were you running the Gnome Shell prior to upgrade ? I see Ubuntu and Ubuntu on Xorg .
Ah, that's it?   I was using 'Ubuntu Gnome' so I guess I already was using Gnome with Ubuntu.  

So, are they the same?  Ubuntu on xorg = Gnome on xorg?   I am just wondering why my program doesn't work properly when I log in the Gnome on xorg session and it's fine when I use Ubuntu on xorg.  However, the main question here is about the differences (between the sessions).   

Even if they are the same or close, I am wondering why they are split up.

---

### Post by ubunt72 on 2018-01-22
> **deadflowr said:**
> Branding.
The Ubuntu version has Ubuntu theming(?) and branding embedded, where as gnome does not.
That answer makes sense to me. :)    I guess I could ask for help about a vpn application that doesn't work when I use the gnome on xorg session versus it working when logging with Ubuntu on xorg but that is beyond the scope (different topic) of this thread, I guess? :)

Thanks for the replies.

---

