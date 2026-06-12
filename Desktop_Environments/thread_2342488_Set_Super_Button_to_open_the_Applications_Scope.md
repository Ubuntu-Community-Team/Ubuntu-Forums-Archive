---
title: "Set Super Button to open the Applications Scope"
date: 2016-11-07
forum: Desktop Environments
---

### Post by darthpenguin on 2016-11-07
Hi Guys,

I've installed Ubuntu 16.04 and I have done a bunch of tweaks to remove all the features I will never use. Like the online accounts integration, most of the lenses, etc. I know that when I press [Super-Key]+[A] that will open the applications lens and list all the installed applications. I'd like to find a way to bring up the applications list in the same way by pressing only the super key and also have the opening of the applications lens be the default behaviour when clicking on the dash button (Ubuntu icon in the dash). I've checked the forums and Google and I just can't seem to find a way to do this.

Any suggestions?

Thanks.

---

### Post by mc4man on 2016-11-09
would be a bit problematic as the shortcuts for these scopes are defined as just the letter, not super+letter.  So if you disabled super in unity you'd lose all super+letter bindings. I guess if you could find or script a dbus command(s) to open the app scope you could do this. (but lose all other current super+

Another way that may work to some extent would be to look at the various settings in dconf-editor > com > canonical > unity > lenses. In screen I've changed 2, always-search & home-lens-default-view to just use applications.scope

This will give just applications shown from clicking on the Dash home icon & tapping super button. The question would be if it persists over time.
(- if not then one could try changing the defaults for the schemas, in screen note the 2nd one I already did so (not bolded.. 
I don't think the home-lens-priority key matters here but could be edited to say just applications.scope

Edit:after editing in dconf a log out/in may be required..

---

### Post by mc4man on 2016-11-10
Plus it not exactly the same as the applications.scope as probably will just list x amount of recently used vs. all installed, ect..

---

### Post by darthpenguin on 2016-11-10
Here is a shot from my dconf-editor
[IMG]http://i.imgur.com/qX7QGBS.png[/IMG]

By disabling and hiding scopes I think I got as close as I'm going to get to my desired result.

This is what I get when I open the dash menu. It defaults to the home scope but only shows applications. It's good enough for me.
[IMG]http://i.imgur.com/9L7HSLg.png[/IMG]

Frankly I do not like the Unity desktop. Mint's default Cinnamon desktop is much better. It just needs a global menu at the top like unity.

---

