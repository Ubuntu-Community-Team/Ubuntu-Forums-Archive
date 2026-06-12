---
title: "Alltray not working in Gutsy?"
date: 2007-10-26
forum: Desktop Environments
---

### Post by david.rahrer on 2007-10-26
I have a fresh install of Gutsy that I am setting up.  I installed Alltray from the Ubuntu respository using synaptic and it appears in the menu under accessories.  However, when I run it, and click on the window to be docked as always, it doesn't do anything.  The cursor turns into an X like it should, but nothing I click on works except cancel on the Alltray app window.

Has anyone else experienced this?  I've found no other references yet.

Thanks!

---

### Post by magikx21 on 2007-10-26
I guess I have a similar issue, I installed Alltray on Feisty and when I open it I just see like an out line of a small window on my desktop. After upgrading to Gutsy still the same. Probably unrelated to yours but an issue with Alltray none the less.

---

### Post by david.rahrer on 2007-10-26
Well, I found a bug report which probably covers it.  Apparently it's Compiz which is now installed by default.  Apparently it still works from the startup script so that's a workaround for now, but if an app becomes undocked, as happens to me occassionaly with Evolution, it won't be as easy to redock.  

[https://bugs.launchpad.net/ubuntu/+source/alltray/+bug/106583](https://bugs.launchpad.net/ubuntu/+source/alltray/+bug/106583)

Thanks for the help.

---

### Post by aspora.isernia on 2007-10-26
> **david.rahrer said:**
> I have a fresh install of Gutsy that I am setting up.  I installed Alltray from the Ubuntu respository using synaptic and it appears in the menu under accessories.  However, when I run it, and click on the window to be docked as always, it doesn't do anything.  The cursor turns into an X like it should, but nothing I click on works except cancel on the Alltray app window.

Has anyone else experienced this?  I've found no other references yet.
!

I have a different behaviour: the "minimize to tray" part works, but the "show" does not. The application is in the systray, but does not comes back: I have to "undock" to see the window again.

---

### Post by david.rahrer on 2007-10-27
I've just run into another odd behavior myself.  On Evolution at least (haven't tested others yet), Alltray docks it fine from the command line or startup script, but when I click on the tray icon to bring Evolution back up, instead it shows up minimized and in focus in the bottom panel.  This only happens after perhaps 5 minutes of leaving it alone after closing to the tray.  It appears Alltray may need some work.

---

### Post by billguy on 2007-10-27
> **aspora.isernia said:**
> I have a different behaviour: the "minimize to tray" part works, but the "show" does not. The application is in the systray, but does not comes back: I have to "undock" to see the window again.

I am experiencing the same issue.  Also, it appears that none of the alltray options work.  (Gusty).

---

### Post by itsjustarumour on 2007-11-09
> **david.rahrer said:**
> I have a fresh install of Gutsy that I am setting up.  I installed Alltray from the Ubuntu respository using synaptic and it appears in the menu under accessories.  However, when I run it, and click on the window to be docked as always, it doesn't do anything.  The cursor turns into an X like it should, but nothing I click on works except cancel on the Alltray app window.

Has anyone else experienced this?  I've found no other references yet.

Thanks!

Another Plus-One for this same problem.  Still looking for a solution that works, will post up if I find one...

---

### Post by snkmad on 2007-11-11
I thought only me was having this problem.
And just now i discovered the "alltray program_name&" way to run it.

---

### Post by sehe on 2007-11-12
Thanks for the pointers! I like Alltray > Kdocker because it will automatically handle the close (X) button to minimize back into the tray :) sweet

I couldn't get it to work on gustry (I didn't try without compiz, because,.... erm... i Like compiz a lot :))

Thanks for the tip pointing to command line usage of alltray, works for me!

---

### Post by david.rahrer on 2007-11-12
Keep an eye out for odd behavior however even when using it on command line, [as I reported above]("http://ubuntuforums.org/showpost.php?p=3643735&postcount=5").  I don't know if that will happen with all programs, but it became obvious on Evolution after a bit.

---

### Post by snkmad on 2007-11-14
I only tested it with vlc, working ok so far.

---

### Post by jw5801 on 2007-12-17
> **david.rahrer said:**
> I've just run into another odd behavior myself.  On Evolution at least (haven't tested others yet), Alltray docks it fine from the command line or startup script, but when I click on the tray icon to bring Evolution back up, instead it shows up minimized and in focus in the bottom panel.  This only happens after perhaps 5 minutes of leaving it alone after closing to the tray.  It appears Alltray may need some work.

I'm also seeing this. Has anyone come upon a solution yet?

---

### Post by david.rahrer on 2007-12-17
I contacted the author and he says he is aware of the issue but doesn't have the time to fix it right now.  I don't know what the ETA might be, but he seemed to know what was causing it so perhaps if he has some spare time we will get this useful tool back!

Perhaps we should all send donations to cheer him on?  I'm game, but I haven't found a place to send them.  I'll try to ask.

---

### Post by jw5801 on 2007-12-17
Cool, thanks. Keep us posted!

---

### Post by david.rahrer on 2008-03-02
Ok, here is some news.  Jochen has replied and told me it will be impossible for him to continue with Alltray and asked if someone would like to continue the work.  I guess anyone  who is serious about it and has the skills, should go to the [Alltray website]("http://alltray.sourceforge.net/") and let him know.

More news, someone named "AZ" has investigated the problems and come up with a possible solution.  I found the debdiff file he is trying to submit for approval in [this thread]("https://bugs.launchpad.net/ubuntu/+source/alltray/+bug/106583").  I figured out how to use a debdiff (never heard of it until now) and created a patched deb to try out.  So far it is working fine for me on Gutsy 32 with Compiz running, i.e. the same setup that make the current version of Alltray go nuts).

I've attached the deb for you to try at your own risk.  I doubt there is much it could harm anyway, but if it works for a number of people that might prove that "AZ" was on the right track with his work.

Good luck, report back to this thread with your results.

**Update:** I apologize, somehow compiz was disabled during my work with this yesterday and that's why it seemed to be corrected.  Please don't bother with this attachment.  I'll try to apply the original diff to the source and build from there.  At least it appears "AZ" is working on it and maybe for Hardy there will be a working version.

---

### Post by in-sanity on 2008-03-05
Hi, I've got mine working on my Ubuntu 7.10 as suggested in the F.A.Q. at [http://alltray.sourcefourge.com](http://alltray.sourcefourge.com)

I've created a file in my home directory and placed the following code:

#!/bin/bash

#thunderbird mail client
alltray evolution &

This is only to start Evolution. Then make the file executable, chmod +x, and add it to you sessions by going to Preferences->Sessions.

Enjoy AllTray.

By the way, I also have activated all the effects in compiz-fusion and is working fine.

---

### Post by david.rahrer on 2008-03-05
The FAQ has always listed this as the way to autostart Alltray with apps loaded.  Mine stopped working correctly with Gutsy 7.10 (see above) with everyone else I have talked with.  As long as I disable effects, i.e. compiz, it works perfectly.  If you are positive compiz is enabled on yours, can you report which video drivers you use?  Does anyone else have this working at all as in-sanity seems to?

PS: You might want to edit your [http://alltray.sourceforge.net/faq.html](http://alltray.sourceforge.net/faq.html) link above, it has a spelling error ;)

---

### Post by jw5801 on 2008-03-05
I never wound up getting it to work. Is there an amd64 .deb of the newer one around anywhere? If there is I can give it a shot and report back.

---

### Post by atoc on 2008-03-08
I got alltray to work under Gutsy by turning off compiz visual effects, running alltray, selecting the apps to be minimized, etc etc and then turning compiz features back on.
[[IMG]http://img329.imageshack.us/img329/6207/screenshotcv9.th.png[/IMG]](http://img329.imageshack.us/my.php?image=screenshotcv9.png)

---

### Post by Deeg on 2008-04-14
I had the same issues with the alltray desktop application. A slight addition to the command line startup approach: I run "nohup alltray evolution > /dev/null&" so that I can close the command window afterwards.

---

