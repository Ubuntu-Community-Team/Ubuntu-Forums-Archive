---
title: "Resolution and refresh rate control for logon screen"
date: 2007-04-27
forum: Desktop Environments
---

### Post by Ianman on 2007-04-27
Hi all,

I hope this is in the right forum but anyway...

I have noticed that if I restart my computer (either from a previous Linux session or from Windows) the screen goes blank when the login screen is loaded. I was having problems with this in Edgy also but I now understand that it happens because the refresh rate of the monitor was not set correctly in the xorg.conf file. I have now rectified the refresh rate but I am under the impression that the refresh rate (which should be set to 60 for my LCD screen) for the login screen is something other than 60.

For some reason my LCD screen will only operate at a refresh rate of 60 (even under Windows). Is there some way that I can force the login screen to show with a refresh rate of 60hz? I am assuming that the xorg.conf file is loaded at this point but still I think the login screen is sometimes running at a different refresh rate than after I have logged in.

Does anyone have any ideas?
Thanks!

---

### Post by orange2k on 2007-04-27
I think it`s probably running at a different resolution - resolution that your monitor can`t handle.
Same thing happened to me, the login screen was running at 1600x1200 even though I set the resolution to be 1280x1024 after login. So I had to edit xorg and eliminate the resolutions I didn`t want to run.

---

### Post by Ianman on 2007-04-27
ok thanks for that. I will remove all the resolution settings that do not apply to my monitor.

---

