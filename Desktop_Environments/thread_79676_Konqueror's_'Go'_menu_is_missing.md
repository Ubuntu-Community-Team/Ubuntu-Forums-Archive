---
title: "Konqueror's 'Go' menu is missing"
date: 2005-10-20
forum: Desktop Environments
---

### Post by oliwally on 2005-10-20
I have upgraded to Breezy after which I had to re-install Konqeror(??? :confused: )  It is working well now but the 'Go' menu and options therein are missing. I had some programs in the 'Autostart' Folder (navigated to through the 'Go' menu) and although that folder still exists on my system, the new version of Konqeror is missing this feature from the previous installation.

Would anyone know what is happening? Do I have to install something extra to add this function?

---

### Post by oliwally on 2005-10-21
bump

---

### Post by shinygerbil on 2005-10-21
If you're talking about the menu that loads when Konqueror starts (i.e. file:///usr/share/apps/konqueror/about/launch.html), then you can get to it by typing about:konqueror in the Address Bar, or if you want it to always load, go to Help -> Konqueror Introduction, then save your view profile.

Hope that's what you were after

steve

---

### Post by oliwally on 2005-10-22
> If you're talking about the menu that loads when Konqueror starts (i.e. file:///usr/share/apps/konqueror/about/launch.html), then you can get to it by typing about:konqueror in the Address Bar, or if you want it to always load, go to Help -> Konqueror Introduction, then save your view profile.

Thanks for helping out. Unfortunately that's not quite what I'm after (but handy to know!!).

I'm talking about a menu button in the 'menubar' somewhere between 'Bookmarks' and 'Tools'. In my previous installation there was a button there called 'Go' and in the drop-down list of that button was a button (folder) called Autostart. It linked to /home/*username*/.kde/Autostart. Although the folder still exists, the button linking to it is no longer there. I don't seem to find any options within konqueror for switching it on either.

Would love to know if anyone has observed the same since upgrading of if there is a solution.

---

### Post by Jens7677 on 2005-10-22
try that:
[http://ubuntuforums.org/showthread.php?t=79941](http://ubuntuforums.org/showthread.php?t=79941)

---

### Post by Staesys on 2005-10-22
**Go Button**

Settings -> Configure Toolbars

At the top, select Location Bar,
on the left, select Go button, Click right arrow button to place it on the right side pane.
on the right, select Go button and click the up arrow however many times you need to place it just below the Location Bar.
Click OK.

**Go Menu**

In my **/home/paul/.kde/share/apps/konqueror** you should find a file called **konqueror.rc** and **konq-kubuntu.rc**. All I did was copy the **konq-kubuntu.rc** to **konq-kubuntu.rc.bak** and make a copy of **konqueror.rc** with the name **konq-kubuntu.rc** and now I have a **Go** menu. You will probably have to end your current session and login again for it to show up, at least I did.

Hope this helps...

---

### Post by oliwally on 2005-10-23
> Go Button

Settings -> Configure Toolbars

That one is okay - it's there by default.

> In my /home/paul/.kde/share/apps/konqueror you should find a file called konqueror.rc and konq-kubuntu.rc. All I did was copy the konq-kubuntu.rc to konq-kubuntu.rc.bak and make a copy of konqueror.rc with the name konq-kubuntu.rc and now I have a Go menu. You will probably have to end your current session and login again for it to show up, at least I did.

On my system that directory didn't have a konq-kubuntu.rc file, and saving the konqueror.rc file as konq-kubuntu.rc didn't do the trick either. Thanks for helping though.

> try that:
[http://ubuntuforums.org/showthread.php?t=79941](http://ubuntuforums.org/showthread.php?t=79941)

Yes, that worked!! I've got my old konqeror setup back. Thank you very much.
I'd love to know why they have changed the new version to be less good? Is there no simpler and more legitimate way (by installing extension perhaps?) to make the new konqeror have the neat features that the old one had.

---

