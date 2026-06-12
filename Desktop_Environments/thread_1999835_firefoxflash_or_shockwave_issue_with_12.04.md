---
title: "firefox/flash or shockwave issue with 12.04"
date: 2012-06-08
forum: Desktop Environments
---

### Post by de Bacon on 2012-06-08
All too often, my system crashes.  I have to wait on things to finish before I dare look at  website that shows video content, news, youtube etc. because often the system crashes.  What I call a crash may be incorrect terminology though, what happens, is it logs out of the current user, going directly to the user account sign in (password entry) where as everything that was on active on the desktop vanishes, no mater what.  

Any ideas?  

Another and separate issue is with Orca (screen reader).  Nearly every time I start it a crash report inquiry comes up, saying "Unity experienced an unexpected crash" or something close to that.  I have finally gotten to the point that I simply close out that popupbox because it always tells me (when attempting to send a report to help) "insufficient information to be helpful."

Truly I think Unity sucks.  I didn't like it when 11.04 first showed it and now I think it even worse than then.

---

### Post by fatalGlory on 2012-06-08
Dropping you back to the login screen (i.e. lightdm) sounds like the X server is crashing.  This is not good, it basically means the graphics subsystem of your computer had a hissy-fit.

If you think Flash's graphics-acceleration might be conflicting with Unity, it wouldn't hurt to try a simpler desktop and see if the conflict goes away.  Try installing Openbox:

```
sudo apt-get install openbox obmenu obconf
```

You should be able to log out then log in again with Openbox instead of Unity as the window manager.  Right-click the desktop to get a menu (which should allow you to open a web browser).  If flash, youtube, etc. works fine then your combination of Unity+graphics drivers may be the problem.

**Alternatively** you can try a different (possibly more stable) version of flash.  The easiest (and most effective) way to do this is by installing FlashAid [[link]](https://addons.mozilla.org/en-US/firefox/addon/flash-aid) in Firefox.  It's an extension that can automatically install the best version of flash for your system and remove all conflicting versions.

---

### Post by de Bacon on 2012-06-09
Well I tried the Flash aid, had it installed long ago though didn't go through the process after the install of precise.  I looked at one thing that used flash, all worked okay but time will tell.  

Oh the issue also did the same with the Rekonq browser.  With the change flash aid made, I am not sure what happens with rekonq??  

As to what I think the issue is ie. flash, I truly have no idea what the issue is, although I believe it occurs when flash is being used, it could also be in conjunction with other programs lurking behind the scenes for all I know.  I'm not big into the why of these things, nor the analysis of the why.  

Thanks for the time to respond with a potential solution to one part of the problems I find with 12.04.  :)

---

