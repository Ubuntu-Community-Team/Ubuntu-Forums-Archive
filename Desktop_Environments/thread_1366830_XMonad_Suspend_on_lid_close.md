---
title: "XMonad Suspend on lid close"
date: 2009-12-28
forum: Desktop Environments
---

### Post by wwbdd on 2009-12-28
In gnome or KDE it's easily configurable if not default behaviour for my laptop (lenovo x61) to suspend to ram upon the lid being closed.  I'm now switching my laptop to xmonad after using and enjoying it on my desktop for quite some time now, but it doesn't suspend/resume with the lid actions anymore.  Is there a way to add such a hook to xmonad such that I can get that behavior back again?

Also, I'm using xmonad straight up, I'm not using it as the window manager for the gnome desktop environment.

Thanks

---

### Post by wwbdd on 2009-12-29
I have come up with a solution that seems to work, though I don't know if it is really the best solution.  I modified the file:

/etc/acpi/actions/lid.sh
```
#!/bin/bash
echo -n mem > /sys/power/state
```

I removed all of the code that was included in this file by default, so who knows what I have done, but it works thus far with just the line above.

---

### Post by hardran3 on 2010-03-28
> **wwbdd said:**
> I have come up with a solution that seems to work, though I don't know if it is really the best solution.  I modified the file:

/etc/acpi/actions/lid.sh
```
#!/bin/bash
echo -n mem > /sys/power/state
```

I removed all of the code that was included in this file by default, so who knows what I have done, but it works thus far with just the line above.

Thanks for your post! this got me on the right track!

If you are running Lucid, open /etc/acpi/lid.sh and  find this line

```
. /usr/share/acpi-support/screenblank
```

and replace it with

```
 echo -n mem > /sys/power/state
```

This takes care of my power management issues on my fluxbox laptop, and doesn't add any more daemons.

---

### Post by de_Selby on 2011-04-17
> **hardran3 said:**
> Thanks for your post! this got me on the right track!

If you are running Lucid, open /etc/acpi/lid.sh and  find this line

```
. /usr/share/acpi-support/screenblank
```

and replace it with

```
 echo -n mem > /sys/power/state
```

This takes care of my power management issues on my fluxbox laptop, and doesn't add any more daemons.

Nice one - I just made a slight change so closing the lid won't put my laptop into sleep if it's charging, but will otherwise. Just replace the line you mentioned with this:

```

Dis=`acpi |cut -f3 -d" "`
if [ "$Dis" = "Discharging," ] ; then
  echo -n mem > /sys/power/state
else
  . /usr/share/acpi-support/screenblank
fi

```

---

