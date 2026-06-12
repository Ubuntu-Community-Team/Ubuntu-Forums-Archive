---
title: "Disable Unity (for custom DE with compiz) from another DE"
date: 2015-02-19
forum: Desktop Environments
---

### Post by quequotion on 2015-02-19
Unity is enabled by default in compiz, which makes it difficult to use compiz with another DE.

In fact, compiz was originally designed to be modular and can still be used with other DE.

To disable unity from a running compiz session (such as Unity itself), [try this.]("http://ubuntuforums.org/showthread.php?t=2124239&p=12550859#post12550859")

This method has the advantage of not having to do this *inside* a broken desktop environment.

0. Log in to a non-compiz DE

1. Set up the custom DE you want to use with compiz (install packages, create files, etc)

2. Open CCSM

3. Click "Preferences ->" in the bottom-left corner of ccsm.

This menu sets how your configuration profiles will be handled.

4. Click the green (+) on the right of "Default" under "Profile"

This copies your current profile into a new one, which needs a name.
There will now be two profiles in the list (the current profile appears at the top of the list, looking like a duplicate).

5. Click "Back" in the bottom left corner of ccsm.

6. Disable Unity
If it doesn't have a checkbox, click on "Ubuntu Unity Plugin" / If it has a checkbox uncheck it and skip to 6.
In the configuration menu, uncheck the "Enable Ubuntu Unity Plugin" box on the left side.

7. Log out of the current session.
This should be all you need to do, but check the standard Ubuntu session once to make sure it isn't broken.

8. Log in to your custom compiz DE.
Everything should be fine, so long as your DE is compatible with compiz.

---

