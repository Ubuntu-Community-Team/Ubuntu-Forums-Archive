---
title: "Gnome desktop doesn't respond, wallpaper gone"
date: 2007-01-23
forum: Desktop Environments
---

### Post by forger on 2007-01-23
I was gonna ask, but the minute I posted, someone helped me to figure out a solution. I now post this as a workaround.

My ubuntu desktop (ubuntu linux 6.10 edgy) is gone,as in background is not showing and no files/folders are visible and i can't right-click, but the gnome-panel works ok.

Here's how it happened:
I was transferring some files on my mobile phone (as a usb device). The first "copying" window was going a bit late than normal. I then started copying another folder into the mobile, which didn't work at all, and it just hanged there. I left it for 15 minutes just to see if it will respond but it didn't.
Then i did ```
killall nautilus
``` and nautilus restarted, but then desktop was gone. I logged out, restarted the gnome desktop with ctrl+alt+backspace but nothing again, even after a restart of the pc it wasn't solved.

Thanks to kelsin from #ubuntu, I figured the solution:
Run ```
gconf-editor
``` and go to apps > nautilus > preferences and see if the "show desktop" is checked.
If it's checked, click on it to uncheck it. Then close the app.
Do ```
killall nautilus
``` and then ```
nautilus
``` and of course close it normally.
Then run gconf-editor again, this time check the "show desktop" option and killall nautilus once more, then do ```
nautilus
``` and close it normally, it will work :)

---

