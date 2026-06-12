---
title: "Shutdown, Restart and Log out missing from the UNity panel (12.04)"
date: 2012-05-02
forum: Desktop Environments
---

### Post by darkmire on 2012-05-02
I've just done a fresh install of 12.04 on my laptop and an upgrade from 11.10 on my desktop.   The upgrade went smoothly (to my surprise) with no problems or issues.  By and large the fresh installation was fine on the laptop except for one annoying thing, and that is that Shutdown, Restart and Logout are all missing from the panel menu although Suspend is there and it works.   I cannot get any of the three to work either in Dash or HUD although I can open a terminal and shut the computer down using sudo shutdown.   I can also get the shutdown menu by pressing the laptop's power button so powering off and restart aren't really a problem and I guess I could live with it. 

But what's more annoying is that if I do restart and log on as a Guest, everything works perfectly with the three items appearing in the menu and all working.  So the problem looks to be with my user setup rather than with the laptop's hardware.  This is where my knowledge runs out.  Is it a bug, is it a configuration problem or is it a conflict and is there a way of fixing it?  It's certainly not a new "feature" as everything functions perfectly on my desktop computer which has largely the same setup except it has Gnome 3 and XFCE set up on it and the laptop is Unity only. Any help would be appreciated.

---

### Post by darkmire on 2012-05-02
Having asked the question after searching around Google for hours, it occurred to me 20 minutes after posting, to have a look at Ubuntu Tweak - and there was the answer.   It was a configuration issue.  For one reason or another, these menu items were disabled on the new install.  There is a tweak listed under Session Indicator that allows these items to be turned on or off.  So on they went - tada!

---

### Post by Denkster on 2012-05-14
I found a solution:
  
[LIST]
[*]Using Software centre,  Remove myunity.
[*]  Start System settings,From the Personal category, choose    Appearance, 

[*]Change Theme to Radiance  (Ambiance was the theme before)
[/LIST]

---

