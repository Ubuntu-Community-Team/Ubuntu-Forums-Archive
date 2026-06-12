---
title: "Disable Unity (for custom DE with compiz)"
date: 2013-03-10
forum: Desktop Environments
---

### Post by quequotion on 2013-03-10
Unity is enabled by default in compiz, which makes it difficult to use compiz with another DE.

In fact, compiz was originally designed to be modular and can still be used with other DE.

0. Set up the custom DE you want to use with compiz and log in to it.

At first, Unity will override your DE and either replace or superimpose itself over whatever panels your DE may provide.

1. Open CCSM

Depending on how broken your DE is at the moment, this could be a challenge. You could use a terminal or even Unity's menu.

2. Click "Preferences ->" in the bottom-left corner of ccsm.

This menu sets how your configuration profiles will be handled.

3. Click the green (+) on the right of "Default" under "Profile"

This copies your current profile into a new one, which needs a name.
There will now be two profiles in the list (the current profile appears at the top of the list, looking like a duplicate).

4. Click "Back" in the bottom left corner of ccsm.

Get ready for a little chaos.

5. Disable Unity
If it doesn't have a checkbox, click on "Ubuntu Unity Plugin" / If it has a checkbox uncheck it and skip to 6.
In the configuration menu, uncheck the "Enable Ubuntu Unity Plugin" box on the left side.
Compiz may try to restart itself and it may crash.

6. Log out of the current session.
This should be all you need to do, but check the standard Ubuntu session once to make sure it isn't broken.

7. Log in to your custom DE again.
Everything should be fine, so long as your DE is compatible with compiz.

---

