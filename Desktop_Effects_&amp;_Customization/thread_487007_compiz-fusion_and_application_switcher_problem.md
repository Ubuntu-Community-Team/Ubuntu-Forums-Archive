---
title: "compiz-fusion and application switcher problem"
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by JonD25 on 2007-06-28
I just installed Compiz-Fusion, and for some reason, the Application Switcher (aka Alt+Tab) is skipping a window every time. So if I only have two windows open, I can never get to the other. Using the shortcut for going backwards works fine, but not forwards. How do I fix this? I couldn't find a setting to change for the life of me.

---

### Post by hyperair on 2007-06-29
Ahaha looks like I wasn't the only one who landed up with that mistake. In CompizConfig Settings manager, go to the switcher plugin, and go to the Actions tab. You'll notice there are two options under Alt+Tab. Disable one of them, according to what you want. ^^

---

### Post by JonD25 on 2007-06-29
Funny. I did that. Still didn't work. Check the screenshot.

Also, it seems like random options are missing here and there. Like, I have the option to change the window close animation, but not the window open animation. I hate my windows zooming in from all over the place, so I change it to a more subtle animation (Glide 2). So my windows will close like I want, but I still get the annoying zoom animation when I open them.

---

### Post by hyperair on 2007-06-29
Uh try updating your system. You might be using an older version of Compiz Fusion, or something of that sort. Also make sure Compiz Fusion starts up before CompizConfig Settings Manager.

---

### Post by JonD25 on 2007-06-29
> **hyperair said:**
> Uh try updating your system. You might be using an older version of Compiz Fusion, or something of that sort. Also make sure Compiz Fusion starts up before CompizConfig Settings Manager.

System is completely up to date.

Compiz Fusion is set to start when I log in, so that shouldn't be a problem either.

---

### Post by hyperair on 2007-06-29
Weird. Well I've had minimal problems with this, and hence minimal experience on fixing it. So.. I'm sorry I can't help you any further. ><

---

### Post by JonD25 on 2007-06-29
Another thing to mention, I think you were right on with the Actions being doubled. Problem is, when I change that one, it doesn't stick. I just looked at it again just now, and even though you can clearly see in my screenshot that I disabled it, it's back to Alt+Tab.

EDIT: Ok, figured it out. All I had to do was double click the first instance and click the default button to reset that one. Turns out it was supposed to be Ctrl+Alt+Tab. Weird, cause I never changed that myself, but clicking default fixed it.

---

### Post by hyperair on 2007-06-29
Aha. I think there's a bug there. See, I've been trying to change the button attributes for the Rotate Cube (Rotate Left and Rotate Right) to Ctrl Alt Mouse4 and Ctrl Alt Mouse5, but they never stick! However, I changed the Alt+Tab one quite some time back.. so may be the bug was introduced only recently?

EDIT: Wait. I think you can do something about it: instead of removing the shortcut, bind it to something else. The second set of Next/Prev Window is for all workspaces. The third one is for current workspace WITHOUT showing the switcher. It just opacifies the windows. I bound the second set to Ctrl+Alt+Tab and Ctrl+Alt+Shift+Tab. Hope that helps.

EDIT: It would seem that the gconf backend for CompizConfig Settings Manager is faulty. So using the flatfile backend solved my problem. Fascinating.

---

### Post by Depressed Man on 2007-06-29
Yeah there are some funky problems with the Settings Manager.. some changes won't stick for me either (like deleting the key command for the alt+tab) so I had to resort to changing it to ctrl+alt+tab. There are some other options that won't stick either.. like invert window snap in wobbly windows plugin.

---

### Post by hyperair on 2007-06-29
Were you using the gconf backend or the flat-file backend? I found that all my problems disappeared when I switched to the flat-file backend ^^

---

### Post by Inxsible on 2007-08-08
had the same problem. Fixed it by clicking the default on the next window.

Funny it was set to Alt + Tab, whereas clicking on Default makes it Ctrl + Alt +Tab :(

Well...works now .Thanks guys

---

