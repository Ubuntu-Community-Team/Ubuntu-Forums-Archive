---
title: "Huge fonts in certain applications"
date: 2009-08-30
forum: Desktop Environments
---

### Post by pveurshout on 2009-08-30
I've set Jaunty to display fonts with a 9pt size and generally everything works fine, however, every now and then I notice that certain applications suddenly have an extremely large font when I start them for the first time after booting (KMess, Skype: it's about 1.5-2x the size I normally use, see screenshot below) or where the font is messed up in some other way (Firefox: both the application font and font used on websites is wrong, and the letter 'k' doesn't display properly. Somewhat similar to [http://ubuntuforums.org/showthread.php?t=1169688]("http://ubuntuforums.org/showthread.php?t=1169688")). This does not affect the window title or anything, only the contents of the window itself. 
The font settings in System/Preferences/Appearance do not appear to change while this happens (it keeps showing 9pt, as it should).

Strangely enough:
[LIST=1][*]Other applications (although I haven't tried them all, of course ;)) work perfectly fine while these three are having problems,
[*]Generally, when I close the application and try again a little while later, the problem mysteriously enough has disappeared all by itself (but today it actually took at least 10 minutes),
[*]Sometimes I can go days without experiencing any of this, but then again it can also happen three times in a row. The annoying part is that I can never be sure it'll fix itself if I simply close the application and restart it a couple seconds later (which usually does the trick).
[/LIST]

Could this be related to using an application called 'preload', which loads frequently used applications into memory automatically (to speed up launching them)? **I don't really know if it makes any sense, but my theory is that KMess, Skype and Firefox are loaded into memory at start-up _before_ Gnome imposes its font settings, thereby not affecting these applications anymore.** Could something like this actually occur? (I'll disable preload anyway and use the system for a couple of weeks to see if anything changes - "unfortunately" I don't experience the problem every time I boot..).

Screenshot:

[http://launchpadlibrarian.net/23230352/Screenshot.png](http://launchpadlibrarian.net/23230352/Screenshot.png)

NOTE: I borrowed this screenshot from someone else. As I only experience these large fonts in certain applications (Nautilus not being one of them) the screenshot is just to give an idea of what happens.

---

### Post by pveurshout on 2009-09-05
I noticed that when this happens, the fonts go back to normal if I just change the application font (under Preferences -> Appearance -> Fonts) to another size and then change it back. I'm fine with this workaround, so anyone reading this thread and offering help: it would absolutely be appreciated, but not really necessary anymore :)

(I marked the thread as solved..is this appropriate in this case, as it actually isn't solved but just not really a problem anymore?)

---

