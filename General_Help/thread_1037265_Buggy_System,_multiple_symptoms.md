---
title: "Buggy System, multiple symptoms"
date: 2009-01-11
forum: General Help
---

### Post by sebastianrimbaud on 2009-01-11
Okay I think it started with me downloading Compiz fusion-icon. Since that's the only major thing I did before it happened.

I had installed it before to play games and even changed by driver from nvidia 177 to 173, but I don't know if those factor in.

Well after that I got this problem that was posted on this board. Very similar at least.

[https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148)

Mine got stuck on the no image resume, normal boot screen and I went with something that got me on startx, but I didn't like it because it didn't go to my user settings so i started and was able to log back into my settings again.

Also I don't remember if I did this worked or not because I tried several solutions. But I remember I did use this one before I did start x.

sudo dpkg-reconfigure -phigh xserver-xorg

Now, after I did all that, my firefox wouldn't work properly and came up with:

Firefox - Component returned failure code: 0x80004005 (NS_ERROR_FAILURE)

I looked around for solutions to that and I even reinstalled my Firefox 3.0, but that didn't fix it. Someone suggested that it maybe be one of the permission users things.

(Forgive me, I've only been an Ubuntu 8.04 user since last month)

Here's a link to the one I used as reference:

[www.ubuntuforums.org/showthread.php?t=873586](www.ubuntuforums.org/showthread.php?t=873586) 

Also when I boot my computer it I found out that it had been showing 

MP BIOS bug: 8254 timer not connected to IO-APIC and already tried these fixes

[www.ubuntuforums.org/showthread.php?t=191355](www.ubuntuforums.org/showthread.php?t=191355)

So far my computer is still working, but my awn manager won't start up, which is annoying and all the firefox back buttons and "show history" doesn't work. 

I think it was worse yesterday, but it seems more bearable. I think it may be related to my permissions access since that was one of the bugs initially. I can't remember it now though. 

Is there a way to find the bug or maybe someone has a solution?

BTW my ubuntu shows a kubuntu boot screen, but looks like ubuntu and uses gnome and I have an AMD 64.

Any help would be appreciated!

---

### Post by sebastianrimbaud on 2009-01-14
I found out that for some reason or maybe I don't remember, but apparently I have both Firefox 3. whatever

and the Beta version as well, could this be the reason my firefox is being loopy?

I started using MidBrowser (dl from the repositories after trying all browsers available) to substitute my Firefox since the back buttons wouldn't work. It's kind sad since I miss all my extensions from firefox like NewBar :-(

Also, I've come to terms with the MP Bios thing. I just wonder if it's something I should worry about in the future?

I also uninstalled compiz doing a complete removal and am  sticking with Cairo dock and metacity. (especially since AWN dock stopped being able to load)

What do you guys think? At least some direction would be helpful. I'm not good with this command stuff and am only beginning to understand Ubuntu.

---

