---
title: "[SOLVED] What happened to Switcher plugins?"
date: 2007-09-07
forum: Desktop Effects &amp; Customization
---

### Post by sultanoswing on 2007-09-07
I installed compiz fusion using the CF Installer script (v3 [http://ubuntuforums.org/showthread.php?t=508769&highlight=compiz-fusion+no+cube](http://ubuntuforums.org/showthread.php?t=508769&highlight=compiz-fusion+no+cube)), and am using the git option.

When I first installed CF last week, it came with two cool window switching plugins: a ring switcher and a window switcher that acted like Apple's cover flow.

Since early this week, however, they no longer appear in the settings manager (despite a complete reinstall, including all settings files, and a coincidental complete reinstall of Ubuntu).

Have these plugins been (temporarily / permanently) removed from the git build? Did Apple's legal department call the compiz guys? Will they be back at some stage? Anyone else notice this?

Thanks!

---

### Post by hyperair on 2007-09-07
Sigh... I suddenly understand more clearly now, what "jumping to conclusions" means. No, it hasn't been removed from the GIT build.

The Compiz Fusion Installer Updater script had always been buggy in the past. If you wish to use a GIT build you should go for Trevino's APT repository, which saves you the time and CPU cycles used for compiling Compiz Fusion. Otherwise I suggest you go and install it manually without the help of that script. One minor error goes wrong in that script and your entire Compiz Fusion's screwed. There's no error checking in that thing.

---

### Post by sultanoswing on 2007-09-07
Ahhh, I had wondered if the script had failed to pick something up. Thanks.

I'll try the repo's, which haven't up until now been kind to me (although I suspect that was due to old versions of Beryl hiding). I'd also considered compiling from source, but hadn't been bothered. Yet. Perhaps if the repos don't work out.

---

### Post by Inxsible on 2007-09-07
Make sure you remove every trace of your current Compiz Fusion install, or it will create problems for you.

---

### Post by sultanoswing on 2007-09-07
> **Inxsible said:**
> Make sure you remove every trace of your current Compiz Fusion install, or it will create problems for you.


Yep that was my previous experience. Pleased to report that with a thorough clean out, Amaranth's repos worked out of the box, and with less stutter than the git build the script was pulling. Thanks again for the suggestions.

EDIT: and the nice switcher plugins are back :)

---

### Post by Inxsible on 2007-09-07
> **sultanoswing said:**
> Yep that was my previous experience. Pleased to report that with a thorough clean out, Amaranth's repos worked out of the box, and with less stutter than the git build the script was pulling. Thanks again for the suggestions.

EDIT: and the nice switcher plugins are back :)
Cool. make sure you mark your thread solved :)

---

### Post by sultanoswing on 2007-09-07
Done.

Only other (very minor) query is what plugin, on mouse-to-screen-edge, displays all windows a-la-OSX's Expose? The compiz fusion 'Expose' shows all 4 cube sides as a film strip, which is nice, but there was also an Expose-OSX-like plugin, but I can't seem to find it on the Repo. version.

EDIT: Sorry about the above superfluous post. I just read the 'Which Repository To Use To Get Compiz Fusion' thread, and I see that Amaranth is missing a few plugins. I'll give Trevino's a try and compare! Thanks again Inxsible for your help on this (and all the other!) compiz threads.

---

### Post by Inxsible on 2007-09-07
> **sultanoswing said:**
> Done.

Only other (very minor) query is what plugin, on mouse-to-screen-edge, displays all windows a-la-OSX's Expose? The compiz fusion 'Expose' shows all 4 cube sides as a film strip, which is nice, but there was also an Expose-OSX-like plugin, but I can't seem to find it on the Repo. version.

EDIT: Sorry about the above superfluous post. I just read the 'Which Repository To Use To Get Compiz Fusion' thread, and I see that Amaranth is missing a few plugins. I'll give Trevino's a try and compare! Thanks again Inxsible for your help on this (and all the other!) compiz threads.
The Expose like plugin is called Scale in Compiz Fusion. and the film-strip type plugin is Expo :)

---

