---
title: "[SOLVED] Some Questions (Awn, Themes)"
date: 2007-12-23
forum: Desktop Effects &amp; Customization
---

### Post by npsken on 2007-12-23
I have recently switched from Windows to Ubuntu Gutsy and got everything set up pretty good; however, I have some questions:

1.) For some reason when I use emerald there is weird swirly stuff surrounding my windows. How do I get rid of this? Screenshot:
[[IMG]http://img210.imageshack.us/img210/1294/screenshotyu2.th.png[/IMG]](http://img210.imageshack.us/my.php?image=screenshotyu2.png)

2.) My windows tend to open covering the awn dock, and I cannot access it; however, I do not want to have the dock spawn over my windows. Is there a way to set a limit as to where the windows can open?

3.) My windows tend to stick the the sides of the screen, which was handy at first, but now it is quite annoying. When I deactivate "place window" or whatever it is, my windows open in a way that the title bar is behind the top panel. Is there a way to fix this?

Thank you for any help provided.

---

### Post by hallstripes2 on 2007-12-23
About the first question, nothings seems too out of the ordinary in your screenshot, so I have to assume you're talking about window shadows. To change that, you have to adjust your actual theme. To do that, go into Emerald, and with your theme selected, click edit theme, and then there's a Frame/Shadow tab within that.

In AWN, I believe there is a way to have either the dock always be on top, or to have your windows open so that they only reach the top of the dock. Unfortunately, I stopped using AWN, so I can't help you with that other than to say there is a way to do it and that it's in the preferences.

For the third question, don't deactivate "Place Windows". It's "Snapping Windows" you have to deactivate. That should fix it. If it doesn't work, I have to recommend getting rid of AWN and just moving your toolbar to the bottom. It's pretty cozy to me after using Windows forever. Screenshot: 
[[IMG]http://img519.imageshack.us/img519/7221/screenshotxu0.th.png[/IMG]](http://img519.imageshack.us/my.php?image=screenshotxu0.png)

This is my first time helping anyone, and I'm relatively new to Linux as well. Good times.

---

### Post by rainwalker on 2007-12-23
I think that thing with the lines in your window border is the Reflection plugin in CCSM (compizconfig-settings-manager is the package name, if you don't have it installed), you can try deactivating that.

Under System > Preferences > AWN Manager, I think checking the box for "Maximized windows don't cover the bar" will fix that issue.

The window snapping is because of the Snapping Windows plugin in CCSM. I agree, it is annoying.

---

### Post by hallstripes2 on 2007-12-23
Wow, I am a buttface. I thought the swirlies were part of your background. Ha.

---

### Post by DaymItzJack on 2007-12-23
1. That looks like the "Reflection" plugin for compiz, try disabling that. CCSM->Effects->Reflection


3. Snapping could also be caused by wobbly windows, it's the first setting "Snap inverted", uncheck that.

---

### Post by npsken on 2007-12-23
Thank you all, everything is working great now!

---

### Post by bharadwaj on 2007-12-24
or click the change background option by right clicking on the desktop and getinto the Visual effects and then set it to none.

---

