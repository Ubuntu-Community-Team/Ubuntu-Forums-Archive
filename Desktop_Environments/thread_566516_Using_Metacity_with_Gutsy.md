---
title: "Using Metacity with Gutsy"
date: 2007-10-03
forum: Desktop Environments
---

### Post by HunterSBuntu on 2007-10-03
Hey, 

I've read that Gutsy will incorporate Compiz Fusion directly in the release, my question is will we be able to disable it and use a more 'vanilla' manager like Metacity?

After having played around with Compiz Fusion on Feisty I wasn't really happy with the performance  with my meager 512MB of RAM, everything seemed a bit sluggish.   I just want to be sure that other options will still work in Gutsy.

---

### Post by miggols99 on 2007-10-03
Yes. There will be an option to turn off "desktop effects" although the defaults are quite nice. No cube. No wobbly windows. Just nice simple effects. Of course you can customise it, but simple eye candy, which doesn't get in the way is very nice.

---

### Post by HunterSBuntu on 2007-10-03
Wow, that was fast.

Gotta love the Ubuntu community.  Thanks.

---

### Post by Bruce M. on 2008-02-20
> **miggols99 said:**
> Yes. There will be an option to turn off "desktop effects" although the defaults are quite nice. No cube. No wobbly windows. Just nice simple effects. Of course you can customise it, but simple eye candy, which doesn't get in the way is very nice.

But turning off "desktop effects" still leaves compiz as the window-manager, it's not replaced with metacity.

**EDIT:**
If you want Metacity - Set it up in Applications > System Tools > Configuration Editor

In Configuration Editor: desktop > gnome > applications > window_manager

Edit the two keys: Current and Default to read: /usr/bin/metacity

I tried using "metacity --replace" but it did NOT change either of these keys

---

