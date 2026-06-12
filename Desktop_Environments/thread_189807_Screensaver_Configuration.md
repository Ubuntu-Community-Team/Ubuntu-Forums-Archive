---
title: "Screensaver Configuration"
date: 2006-06-05
forum: Desktop Environments
---

### Post by WrathofthePenguin on 2006-06-05
One of the things I noticed right away when I upgraded to Dapper was that I no longer had the ability to configure individual screensavers. It is so bad that I can't even select which screensavers I want to run in random. This is a surprising leap backwards.

I've figured out how to remove screensavers that I don't ever want to run (I delete them in the usr/share/gnome-screensaver/themes directory), but I have been unable to find a way to configure the individual screensavers. How do I change the settings of the individual screensavers? I'm assuming that I'll have to edit a config file, but I don't know which one. Anybody played with this yet?

---

### Post by franestepona on 2006-06-05
I have also noticed that the power preferences are not longer configurable from there. I mean to shut down the monitor (not just blank). Looks like the previous screensaver configurator program was much better.

---

### Post by shattenjagger on 2006-06-05
On another screensaver note, after the upgrade from breezy to dapper, a bunch of the screensavers disapeared as well.

---

### Post by matthew on 2006-06-05
This was bugging me as well. I figured out what to do.

First, uninstall the package "gnome-screensaver" using synaptic or apt-get or aptitude.

Second, make sure the package "xscreensaver" is installed (you may want to install the other packages that go with it like "xscreensaver-data".

You can start the dialog box you remember from Breezy at the command line with the command "xscreensaver-demo"

Finally, you can fix the link in your menu by using Applications->Accessories->Alacarte Menu Editor and change the preferences for System->Preferences->Screensaver from "gnome-screensaver" to "xscreensaver-demo" by doing a right click on "Screensaver" in the list and choosing "Properties."

Sorry this isn't a better detailed "how-to." If anyone gets the urge to type up a clearer step-by-step and submit it as a how to I'm sure it would be welcome...with the Dapper release we're pretty busy.

---

### Post by Stackmouse on 2006-06-05
matthew was faster, and his "how-to" is better :)

---

### Post by franestepona on 2006-06-05
[QUOTE=matthew]This was bugging me as well. I figured out what to do.

First, uninstall the package "gnome-screensaver" using synaptic or apt-get or aptitude.

Second, make sure the package "xscreensaver" is installed (you may want to install the other packages that go with it like "xscreensaver-data".

You can start the dialog box you remember from Breezy at the command line with the command "xscreensaver-demo"

Finally, you can fix the link in your menu by using Applications->Accessories->Alacarte Menu Editor and change the preferences for System->Preferences->Screensaver from "gnome-screensaver" to "xscreensaver-demo" by doing a right click on "Screensaver" in the list and choosing "Properties."

Sorry this isn't a better detailed "how-to." If anyone gets the urge to type up a clearer step-by-step and submit it as a how to I'm sure it would be welcome...with the Dapper release we're pretty busy.[/QUOTE]

Thanks!! works perfectly!

---

### Post by WrathofthePenguin on 2006-06-05
Ok Matthew - quick question. I went to uninstall this in Synaptic and it's telling me that it wants to mark ubuntu-desktop for removal also. Do I really want to do this, or is there a better way?

[QUOTE=matthew]This was bugging me as well. I figured out what to do.

First, uninstall the package "gnome-screensaver" using synaptic or apt-get or aptitude.

Second, make sure the package "xscreensaver" is installed (you may want to install the other packages that go with it like "xscreensaver-data".

You can start the dialog box you remember from Breezy at the command line with the command "xscreensaver-demo"

Finally, you can fix the link in your menu by using Applications->Accessories->Alacarte Menu Editor and change the preferences for System->Preferences->Screensaver from "gnome-screensaver" to "xscreensaver-demo" by doing a right click on "Screensaver" in the list and choosing "Properties."

Sorry this isn't a better detailed "how-to." If anyone gets the urge to type up a clearer step-by-step and submit it as a how to I'm sure it would be welcome...with the Dapper release we're pretty busy.[/QUOTE]

---

### Post by oyvindaa on 2006-06-05
[QUOTE=WrathofthePenguin]Ok Matthew - quick question. I went to uninstall this in Synaptic and it's telling me that it wants to mark ubuntu-desktop for removal also. Do I really want to do this, or is there a better way?[/QUOTE]

It's not a real package I think, so it won't harm your system.
I did the same earlier today and everything's fine.
Go for it mate!

---

### Post by matthew on 2006-06-05
[quote=WrathofthePenguin]Ok Matthew - quick question. I went to uninstall this in Synaptic and it's telling me that it wants to mark ubuntu-desktop for removal also. Do I really want to do this, or is there a better way?[/quote]You can remove that package safely...just remember to reinstall it before you do a dist-upgrade. Interesting, though, Synaptic didn't prompt me about removing ubuntu-desktop.

You could also try skipping the gnome-screensaver removal step, stop it every time you do a restart and then run xscreensaver-demo. That would be a pain, though.

---

### Post by vayde on 2006-06-05
Going back to xscreensaver really bogged my system down, which shouldn't happen with an inspiron 9300 2Ghz proccessor, 1G ram.  Or should it?

I ended up going back to gnome-screensaver and just removing the ones I didn't like from /usr/share/gnome-screensaver/themes

---

### Post by OtubrabNad on 2006-06-05
Thanks! Gnome screensaver is horrible!!

However I have a question. Xscreensaver has power saver options, whereas the new distribution divides up the the screensaver and power management tool. Since I now have both xscreensaver and the gnome power manager installed, which will take precedent?

---

### Post by matthew on 2006-06-06
[quote=vayde]Going back to xscreensaver really bogged my system down, which shouldn't happen with an inspiron 9300 2Ghz proccessor, 1G ram.  Or should it?[/quote]I thought I observed the opposite effect on my system, but I may have been dreaming. In any case I haven't noticed any real significant change faster or slower.

---

### Post by matthew on 2006-06-06
[quote=OtubrabNad]However I have a question. Xscreensaver has power saver options, whereas the new distribution divides up the the screensaver and power management tool. Since I now have both xscreensaver and the gnome power manager installed, which will take precedent?[/quote]Great question. I'm not sure which will take precedent. I've had mine running for about 24 hours after making the change with no negative side effects. I suppose we could just change the two power management schemes and see which one takes effect. 

There is also the possibility that they are merely two different interfaces for the same basic thing (ACPI, I would guess) and so whichever was run most recently could be the one in effect. ??

---

### Post by nocloud on 2006-06-06
has there been a fix found for the kubuntu monitor power off time option not being retained after a reboot?

---

### Post by MorphWVUtuba on 2006-06-06
[QUOTE=matthew]This was bugging me as well. I figured out what to do.

First, uninstall the package "gnome-screensaver" using synaptic or apt-get or aptitude.

Second, make sure the package "xscreensaver" is installed (you may want to install the other packages that go with it like "xscreensaver-data".

You can start the dialog box you remember from Breezy at the command line with the command "xscreensaver-demo"

Finally, you can fix the link in your menu by using Applications->Accessories->Alacarte Menu Editor and change the preferences for System->Preferences->Screensaver from "gnome-screensaver" to "xscreensaver-demo" by doing a right click on "Screensaver" in the list and choosing "Properties."

Sorry this isn't a better detailed "how-to." If anyone gets the urge to type up a clearer step-by-step and submit it as a how to I'm sure it would be welcome...with the Dapper release we're pretty busy.[/QUOTE]
Very helpful & appreciated.  I would add it might be a little easier to make the change to the alacarte menu first.  Then when you uninstall gnome-screensaver, it won't delete the entry in the menu editor.

---

### Post by WrathofthePenguin on 2006-06-07
I did it and it worked fine, except for one thing. I can do everything I complained about before, but now the really cool new screensavers are not available. I'm crushed. What kind of sick people did this?!? Are they reading this even now, snickering to themselves at my torment?

Getting back to serious discussion - it works great, and I think I can live with the few lost screensavers. Thanks for all your help!

[QUOTE=matthew]You can remove that package safely...just remember to reinstall it before you do a dist-upgrade. Interesting, though, Synaptic didn't prompt me about removing ubuntu-desktop.

You could also try skipping the gnome-screensaver removal step, stop it every time you do a restart and then run xscreensaver-demo. That would be a pain, though.[/QUOTE]

---

### Post by blueturtl on 2006-06-07
There is a bug in xscreensaver-demo that causes the configuration window to completely lock up or at least slow to a crawl when you're transferring data to an external USB hard-disk (not a memory stick). This bug was evident in both Breezy and Hoary on my system. Maybe the devs saw an easy way out by replacing the faulty package?

---

### Post by missmoondog on 2006-06-10
[QUOTE=OtubrabNad]Thanks! Gnome screensaver is horrible!!

However I have a question. Xscreensaver has power saver options, whereas the new distribution divides up the the screensaver and power management tool. Since I now have both xscreensaver and the gnome power manager installed, which will take precedent?[/QUOTE]

going through this "how to" now. worked great. thanks for that.

why did they split up the power management and screensaver tools though? i switch between never and 1 minute quite often during the course of the day and the extra clicks stink! ](*,)

---

### Post by ayoli on 2006-06-10
[QUOTE=matthew]You can remove that package safely...just remember to reinstall it before you do a dist-upgrade. Interesting, though, Synaptic didn't prompt me about removing ubuntu-desktop.

You could also try skipping the gnome-screensaver removal step, stop it every time you do a restart and then run xscreensaver-demo. That would be a pain, though.[/QUOTE]
i skip the gnome-screensaver removal step but uncheck the /apps/gnome_settings_daemon/screensaver/start_screensaver key to avoid stopping it each time i restart, and add to session startup prog (preferences -> session):  xscreensaver --no-splash

---

### Post by matthew on 2006-06-10
[quote=ayoli]i skip the gnome-screensaver removal step but uncheck the /apps/gnome_settings_daemon/screensaver/start_screensaver key to avoid stopping it each time i restart, and add to session startup prog (preferences -> session):  xscreensaver --no-splash[/quote]Good idea!

---

### Post by clparker on 2006-06-15
Yeah, I was very frustrated by this, is this a GNOME problem or an UBUNTU problem, and he's right, this is a HUGE leap backwards, its almost like somebody's trying to dumbdown ubuntu.

"ANGER AND RAGE"

JMHO

---

### Post by delfick on 2006-06-17
i agree

---

### Post by anubis3000bc on 2008-05-29
That's funny i need help to now because i followed that path to get to the theme folder and it's not even there to begin with hmmmmmmmmmmm help meeeeeeeeeeeeeeeeeeeeeeee.

---

### Post by wootah on 2008-05-29
> **anubis3000bc said:**
> That's funny i need help to now because i followed that path to get to the theme folder and it's not even there to begin with hmmmmmmmmmmm help meeeeeeeeeeeeeeeeeeeeeeee.
This thread is over two years old. I don't even know if it still applies anymore...

---

### Post by Joeb454 on 2008-05-29
It most likely doesn't

---

### Post by ugm6hr on 2008-05-29
> **anubis3000bc said:**
> That's funny i need help to now because i followed that path to get to the theme folder and it's not even there to begin with hmmmmmmmmmmm help meeeeeeeeeeeeeeeeeeeeeeee.

Moderator input: Please start a new thread describing your exact problem.  As mentioned, the details in this thread are outdated, and may not be relevant.

Thread closed.

---

