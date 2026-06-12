---
title: "Deadkeys are not my friend."
date: 2009-01-21
forum: General Help
---

### Post by OboeNerd on 2009-01-21
I've had bad experiences with deadkeys before, and I want to find a way to exterminate them.  Adding the "Xkbvariant" "nodeadkeys" option doesn't help.

Hitting the apostrophe adds an ´ accent to the following character, like é, etc.
Then there's " which ends up as ¨

I heard this is a problem with a GNOME override, but I can't find a dead keys option in the gnome settings.

This isn't the worst problem in the world, but I'd at least like the freedom to easily type apostrophes, quote marks, etc. ;)

---

### Post by OboeNerd on 2009-01-21
Now I'm getting this dialog:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

-----
And as suggested, I'll post the results:

```

$xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "us", "nodeadkeys", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "us", "nodeadkeys", ""


$gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
  layouts = [us  nodeadkeys,us  altgr-intl]
  model = pc105
  options = [grp grp:alts_toggle,Compose key   compose:ralt]
  overrideSettings = true
```

I noticed some inconsistency, the first command returns pc104, when the other returns 105.  I'll do an x restart right now and see what happens.

Hopefully more responses can come with this info.

---

### Post by jespdj on 2009-01-21
So you want to get rid of the dead keys? Aren't you making this much more complicated than necessary?

You don't need to mess with X or GNOME configuration files. Just go to System > Preferences > Keyboard. Select the Layouts tab. Set your keyboard to "USA". (Click "Add..." if it isn't listed, and add the "USA" layout. Remove other layouts that you don't want, such as "USA International (with dead keys)").

---

### Post by OboeNerd on 2009-01-21
The problem is that whenever I try to make a change in the settings, I get an error message as explained above.

I'll restart X again and see if that works...

Still not working :(

waitwaitwait....

That was weird.  Now it's working fine.

.....

Looks like the problem solved itself.  Thanks for your help!

;)

---

