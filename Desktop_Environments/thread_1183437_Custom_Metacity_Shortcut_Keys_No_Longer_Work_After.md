---
title: "Custom Metacity Shortcut Keys No Longer Work After Upgarded to Jaunty"
date: 2009-06-10
forum: Desktop Environments
---

### Post by Gias Kay on 2009-06-10
This is what I am talking about:

[http://www.zolved.com/synapse/view_content/27971/How_to_create_custom_shortcut_keys_in_Ubuntu_](http://www.zolved.com/synapse/view_content/27971/How_to_create_custom_shortcut_keys_in_Ubuntu_)

I created a few shortcuts like <Control><Alt>e to open gedit for example. Worked great in Intrepid. But after I upgraded to Jaunty yesterday, these shortcut keys have mysteriously stopped working for me. I tried opening gconf-editer, deleting and re-defining the keys, but to no avail.

Anyone suffering from the same issue? Or any idea on how to fix it? This is a very convenient feature :(

---

### Post by kpkeerthi on 2009-06-10
Do you have compiz (desktop effects) enabled?

---

### Post by Gias Kay on 2009-06-10
> **kpkeerthi said:**
> Do you have compiz (desktop effects) enabled?

Yes I have, I enabled some extra effects back when I was in Intrepid and everything worked fine then.



EDIT:

Wow, I set Visual Effects to None and the problem is gone... so this is a known bug?
Is there any way to fix it with Visual Effects set to Extra, on the other hand?

---

### Post by kpkeerthi on 2009-06-10
It is not a bug.

If you are using desktop effects, then metacity no longer manages your windows. Your window manager would be compiz. You need to install **compizconfig-settings-manager** (ccsm) from Applications -> Add/Remove to customize Compiz.

Customize the keyboard shortcuts from System -> Preferences -> ccsm -> Commands / Keybindings tabs. First add a Command under **Commands** and then bind it to a key-combo under **Key Bindings**.

---

### Post by Gias Kay on 2009-06-13
Works great =)

Seems like there's a little bug during the upgrade: they actually ported the metacity setting into compiz already, but they forgot to enable it (the Commands option was not checked in ccsm).

---

### Post by arglborps on 2009-06-17
Well this didn't help me much, because I wanted to add and/or change some of the menu shortcuts for Nautilus (and other gtk+ apps) on the fly.

So what am I supposed to input into the "Edit Run command 0" dialogue field?

---

