---
title: "Making Fluxbox work together with Gnome?"
date: 2009-03-20
forum: Desktop Environments
---

### Post by Imperivm on 2009-03-20
I've googled a lot but as of yet have not found a solution to my problem, hence this topic. Does anyone know of a way to make Fluxbox work properly with Gnome's GTK themes?

I've run "gnome-appearance-settings &" in Fluxbox's startup file, making gnome-appearance-settings run on Fluxbox startup (manually closing it), rendering the GTK applications "prettier" (Nautilis, Firefox, GParted, etc).

When trying to find a way to circumvent this, I installed gtk-chtheme, which kind of worked. But with that, there are applications (e.g. GParted) that are not themed, and I am confined to existing themes or making my own.

The difference in RAM usage between gtk-chtheme and gnome-appearance-properties is not large enough (less than 5%) to justify the "lack" of options gtk-chtheme offers. And as much as I like Fluxbox, the "ugly" GUI (whatever you do, selections will always be blue; font differences, etc) puts me off.

Is there any way I could run gnome-appearance-properties, have it apply its settings (by running, basically), and then kill itself without noticing it?

Or, alternatively, is there any other way I could apply my gnome-appearance-settings to the applications on startup without having to do it manually every time I boot up? (Electricity is expensive, so I've been turning off my computers when not in use :(.)


[edit]
Oh, and even after uninstalling gtk-chtheme and running gnome-appearance-properties in the startup file again, the theming is FUBARed. Fonts set in gnome-appearance-properties are ignored for GTK apps and for example Firefox has still a lot of the "Inverted" them about it.

I'm going to do a complete re-install in the next few weeks when I do an overhaul of the entire network, though, so I can bear the pain for now :p

---

### Post by kerry_s on 2009-03-21
i'm not sure what you mean?
for root programs(sudo), you need to link or copy your gtkrc-2.0 to /root.

i use lxapperance for my wm(jwm). i copy the gtkrc-2.0 to root cause i usually set it to different settings.

---

### Post by RedSquirrel on 2009-03-21
> **Imperivm said:**
> Oh, and even after uninstalling gtk-chtheme and running gnome-appearance-properties in the startup file again, the theming is FUBARed. Fonts set in gnome-appearance-properties are ignored for GTK apps and for example Firefox has still a lot of the "Inverted" them about it.


gtk-chtheme creates the text file [COLOR=Blue]~/.gtkrc-2.0[/COLOR]. The contents of this file are the theme settings you chose with gtk-chtheme. If you want to use gnome-appearance-properties, you should remove or rename that file (if you have not already done so).

For example, to rename:
```
mv ~/.gtkrc-2.0 ~/.gtkrc-2.0.off
```

---

### Post by Imperivm on 2009-03-21
> you should remove or rename that file (if you have not already done so). #-o, of course!

> **kerry_s said:**
> i'm not sure what you mean?
for root programs(sudo), you need to link or copy your gtkrc-2.0 to /root.

i use lxapperance for my wm(jwm). i copy the gtkrc-2.0 to root cause i usually set it to different settings.I'll have to test it again to see what exactly I meant, apart from "certain applications not being themed" my mind has lost the details.

I'll copy gtkrc-2.0 to root and see if that makes things better.


What I ideally would like to do is to run gnome-appearance-settings when Fluxbox starts, and then have it automatically close itself - so, the settings are applied but the Appearance window isn't visible on the desktop and does not need to be manually closed. I've tried

"gnome-appearance-properties &
 killall gnome-appearance-properties"

but that didn't work. At the moment it seems the easiest/best solution to use gnome-appearance-settings, because I've found the settings easier to change without relying on themes so much.


Thanks for the replies!


[edit]
Adding .gtkrc-2.0 to /root did the trick to theme the sudo applications, too, so that's out of the way.

Now to learn how to edit the theme to my liking :D

---

### Post by RedSquirrel on 2009-03-21
> **Imperivm said:**
> What I ideally would like to do is to run gnome-appearance-settings when Fluxbox starts, and then have it automatically close itself - so, the settings are applied but the Appearance window isn't visible on the desktop and does not need to be manually closed. I've tried

"gnome-appearance-properties &
 killall gnome-appearance-properties"

but that didn't work. At the moment it seems the easiest/best solution to use gnome-appearance-settings, because I've found the settings easier to change without relying on themes so much.

Here is some code from the Openbox autostart.sh file that allows you to theme everything the way it looks in GNOME while running Fluxbox:

```
# D-bus
if which dbus-launch >/dev/null && test -z "$DBUS_SESSION_BUS_ADDRESS"; then
       eval `dbus-launch --sh-syntax --exit-with-session`
fi

# Make GTK apps look and behave how they were set up in the gnome config tools
if test -x /usr/libexec/gnome-settings-daemon >/dev/null; then
  /usr/libexec/gnome-settings-daemon &
elif which gnome-settings-daemon >/dev/null; then
  gnome-settings-daemon &
```The second part is obviously the most important. I don't know if you need to be running dbus as well. I included it here anyway and you can try it both with and without dbus to see what works for you. I don't use GNOME very much at all and I don't have it installed at the moment (nor Ubuntu, for that matter :)), so I can't test this, but I know it worked pretty well in the past.

And note that it's **gnome-settings-daemon** you want, not gnome-appearance-properties. :D

---

