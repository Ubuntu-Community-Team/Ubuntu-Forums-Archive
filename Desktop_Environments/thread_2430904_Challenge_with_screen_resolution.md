---
title: "Challenge with screen resolution"
date: 2019-11-09
forum: Desktop Environments
---

### Post by dwlamb on 2019-11-09
If this is not the correct forum for this post, my apologies.  I think  this is a KDE issue for the challenge I am experiencing arises after I  enter my login and KDE settings are loaded from my profile.

The  challenge I'm experiencing is that my two displays are rendering at  1960x1120.  One is scaling properly to 1920x1080 while the other  presents a distorted display area. 

I've included two screen captures [https://pasteboard.co/IFEr5rl.png](https://pasteboard.co/IFEr5rl.png) and [https://pasteboard.co/IFErJy6.png](https://pasteboard.co/IFErJy6.png).  They both show the dimensions are 1960x1120.  At least, that is what is  happening according to the package Spectacle. The one with a red  outline on a web page shows what is visible on the screen.  The one with  no red outline was captured from the screen that is rendering properly  and shows the settings as configured for the screen that is not scaling  properly.

How do I fix this? The x.org config file is no longer  used by default since Ubuntu 16, I believe. Is this a case where  creating an x.org config file will solve the problem? Is there another  file I can manually edit to render the desired  output. The screen that  is not rendering properly is actually a TV made by Insignia that I'm  using in VGA mode.  The maximum resolution is 1920x1080. The screen that  is rendering as desired is an Acer.

Thank you for taking the time to read this.

---

### Post by SeijiSensei on 2019-11-09
Did you set the resolution in System Settings > Displays?

---

### Post by dwlamb on 2019-11-09
Yes.  As indicated in one of the screenshots I shared the settings under System Settings > Displays.  Each of the displays is the highest possible, 1920x1080.  I don't understand how the screenshots can be 1960x1120 when that is in excess of the max resolution under System Settings > Displays.

---

### Post by CatKiller on 2019-11-09
> **dwlamb said:**
>  I don't understand how the screenshots can be 1960x1120 when that is in excess of the max resolution under System Settings > Displays.

That's a 20 pixel margin around each window edge, exactly of the sort that you might get if, for example, window edges had a shadow effect that was being grabbed by whatever is taking the screenshot.

---

### Post by CatKiller on 2019-11-09
> **dwlamb said:**
> The screen that  is not rendering properly is actually a TV made by Insignia that I'm  using in VGA mode.

TVs are even worse than monitors (many of which are already pretty bad) at providing accurate EDID responses. VGA adaptors generally don't include the connections to allow EDID to pass through.

EDID is how resolutions are automatically set: the display says the resolutions it can do, and the computer sets the resolution to one of those. Without that information, the computer has to guess. It is often not a good guess.

---

### Post by SeijiSensei on 2019-11-09
If you connect to the TV with HDMI, do you still have this problem?

---

### Post by dwlamb on 2019-11-17
Sorry it has been a week since starting this thread.  I ended up having to move components from my original system to a new bare bones system due to a separate issue.  This did not mean a new video card. So I was presented with the same issue as the original post.

Yes, I still had the same issue using HDMI. 

Troubleshooting this, I tried a variety of methods.  Setting this monitor as 0-1920, 1920-3840, HDMI or VGA.  It has no DVI.  A major hassle was getting KDE to forget a previous connection of this monitor to the system.  The best way to start with a new set-up was only connect this monitor physically before introducing the second.

In the end, I learned:  The troublesome monitor can only be to the left of the second and 0-1920.  After some searching, I found the remote control for it.  Through menus on that I rediscovered an option to automatically fine-tune the resolution when connected only in VGA.  This option is only available in VGA mode.  It would not correct the resolution problem depicted in one of the screenshots of the original post when it was 1920-3840, but it would fix minor problems like 10 pixels bleeding off-screen to the right and bottom when initially activated with a second monitor.  All is well now, thankfully.

Thanks to all who provided input.

---

