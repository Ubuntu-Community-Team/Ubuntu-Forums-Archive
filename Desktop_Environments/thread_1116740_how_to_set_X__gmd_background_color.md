---
title: "how to set X / gmd background color?"
date: 2009-04-05
forum: Desktop Environments
---

### Post by akos.maroy on 2009-04-05
I'm having an issue setting the background color of the gdm application. this is the color that appears _after_ one has entered his username / password, but before the users on gnome theme kicks in.

on ubuntu 8.10, this appears to be the brownish color of the default Human theme. if I ask gdmflexiserver, it tells me about this color indeed:

```
$ gdmflexiserver --command="GET_CONFIG greeter/GraphicalThemedColor $DISPLAY"
OK #dab082
```

now, I tried to change this in a number of ways, but to no avail. I replaced this color code in /etc/gdm/gdm.conf:

```
BackgroundColor=#dab082
GraphicalThemedColor=#dab082
```

I also replaced references to "Human" (the default unbuntu 8.10 gdm theme) to the gdm theme I'm using in the same config file:

```
GtkGtktheme=Human
GraphicalTheme=Human
```

naturally, the gdm theme is set to my preferred theme already, instead of Human.

but still, after I type in my login details, I still get the old default brownish color. and the response from the gdmflexiserver command is also the same.

how / where do I set this background color preference?

---

### Post by _Purple_ on 2009-04-05
Go to System > Preference > Appearance.

You can change it from Colors in Background tab.

---

### Post by akos.maroy on 2009-04-06
> **_Purple_ said:**
> Go to System > Preference > Appearance.

You can change it from Colors in Background tab.

yes, of course this was one of the first things I did. unfortunately this one doesn't have any effect :(

but, the change in setting in /etc/gdm/gmd.conf did have an effect after all, only after a reboot though.

---

### Post by mcduck on 2009-04-06
The GUI way is System/Administration/Login Window. You can set the color on local-tab (the same place where GDM themes are selected).

---

### Post by akos.maroy on 2009-04-06
> **mcduck said:**
> The GUI way is System/Administration/Login Window. You can set the color on local-tab (the same place where GDM themes are selected).

thanks - indeed, this solution works fine!

---

