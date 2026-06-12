---
title: "Power Problems"
date: 2009-01-30
forum: Desktop Environments
---

### Post by bconover on 2009-01-30
When I press the power button on my laptop, it does not give me an options screen (Shutdown, Restart, Log Out, etc..) but instead just immediately shuts down.

I started out with GNOME on this laptop, under Ubuntu 8.10. However, I recently switched to KDE 4.1.3. When I was running GNOME, when I pressed my power button, I got this nice little menu that asked me what exactly I wanted to do, Shutdown, Restart, Log Out, or Suspend.

However, under KDE 4.1.3 I noticed right away that this option did not seem to be included. I searched through the System Settings menu, but could find no option that would enable this. Unlike the gnome-power-manager, guidance-power doesn't seem to offer such an option.

I have now upgraded to KDE 4.2, and saw the Power Manager option in the Advanced System Settings. There would seem to be an option that would enable such a choice-menu to be brought up when I press the power button, but changing these settings to bring up the menu does not fix my problem.

I assume there is some other piece of code that is telling my laptop to shutdown on the event of my power button being pressed. Somehow I need to either disable this code or change it to bring up the desired menu. However, tracing the power button press event to powerbtn.sh in /etc/acpi has done me no good. I am an amateur at writing bash script.

Here is /etc/acpi/events/powerbtn, which I think is what is triggered when I press the button:

```
# /etc/acpi/events/powerbtn
# This is called when the user presses the power button and calls
# /etc/acpi/powerbtn.sh for further processing.

# Optionally you can specify the placeholder %e. It will pass
# through the whole kernel event message to the program you've
# specified.

# We need to react on "button power.*" and "button/power.*" because
# of kernel changes.

event=button[ /]power
action=/etc/acpi/powerbtn.sh
```

And here is /etc/acpi, which would appear to be run by the above event:

```
#!/bin/sh
# /etc/acpi/powerbtn.sh
# Initiates a shutdown when the power putton has been
# pressed.

# Skip if we just in the middle of resuming.
test -f /var/lock/acpisleep && exit 0

# If gnome-power-manager, kpowersave or klaptopdaemon are running, let
# them handle policy This is effectively the same as 'acpi-support's
# '/usr/share/acpi-support/policy-funcs' file.

if pidof gnome-power-manager kpowersave > /dev/null ||
  (pidof dcopserver > /dev/null && test -x /usr/bin/dcop && /usr/bin/dcop kded kded loadedModules | grep -q klaptopdaemon) ; then
    exit
fi

# Otherwise, if KDE is found, try to ask it to logout.
# If KDE is not found, just shutdown now.
if ps -Af | grep -q '[k]desktop' && pidof dcopserver > /dev/null && test -x /usr/bin/dcop ; then
    KDESES=`pidof dcopserver | wc -w`
    if [ $KDESES -eq 1 ] ; then
        # single KDE session -> ask user
        /usr/bin/dcop --all-sessions --all-users ksmserver ksmserver logout 1 2 0
        exit 0
    else
        # more than one KDE session - just send shutdown signal to all of them
        /usr/bin/dcop --all-sessions --all-users ksmserver ksmserver logout 0 2 0 && exit 0
    fi
fi

# If all else failed, just initiate a plain shutdown.
/sbin/shutdown -h now "Power button pressed"
```



Any help as to how to work with this to achieve my desired results is greatly appreciated! This isn't the biggest problem, I know, it's just that often I find it more convenient to press the power button and select my option than to open the Kickoff menu and navigate over to Leave, and then choose my option. Thanks!

-bconover

*Running KDE 4.2.00 over Ubuntu 8.10 (Intrepid Ibex).*

---

### Post by CyDharttha on 2009-02-18
Hey, I'm running into this problem as well, on my TV PC. Would have never noticed, but my little boy found the power button, and so it goes.

It looks like those files you're listing maybe aren't ready for KDE 4.1x/4.2 yet? I only glanced. I think what I'll do to fix this for now, is comment out that last line in /etc/acpi that performs a 'shutdown -h now'.

Thanks for posting on the problem, hopefully I can get some time to make sure this bug has been properly filed.

Thanks!

---

### Post by olifhar on 2009-03-02
Do the menu entries in the leave option even work for you guys? None of them, even Logout, does anything when I click them. Besides doing shutdown from command line, power button is now only way to shutdown once logged into KDE.

(Another thread [here]("http://kubuntuforums.net/forums/index.php?topic=3101178.0"), with similar puzzlement and lack of solution...)

---

