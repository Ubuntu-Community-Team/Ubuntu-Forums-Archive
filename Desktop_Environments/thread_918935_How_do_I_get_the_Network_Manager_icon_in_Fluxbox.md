---
title: "How do I get the Network Manager icon in Fluxbox?"
date: 2008-09-13
forum: Desktop Environments
---

### Post by stealth17 on 2008-09-13
How can I get the network manager icon to show up in Fluxbox? I really like the new network manager for the wireless, but I can't get it to show up in Fluxbox.

---

### Post by Anzan on 2008-09-15
Just put

nm-applet &

in your startup file.

---

### Post by stealth17 on 2008-09-16
> **Anzan said:**
> Just put

nm-applet &

in your startup file.

Works perfect. How about the power applet? Is there a list of applets somewhere because I tried finding it using tab tab in the terminal but cannot locate the command.

Thanks!

---

### Post by Anzan on 2008-09-17
Look in /usr/bin for the real name of applications. For example OpenOffice Writer is oowriter.

I'm on my desktop box rather than a laptop right now so I don't have the battery applet in my startup file but I think it's called gnome-power-manager.

---

### Post by leef on 2008-09-17
The power management tray icon is

gnome-power-manager &

another useful one is the update manager (for security etc);

update-notifier &

---

### Post by stealth17 on 2008-09-18
> **leef said:**
> The power management tray icon is

gnome-power-manager &

another useful one is the update manager (for security etc);

update-notifier &

is seems the only way I can get gnome-power-manager to start is if I use sudo first.... Why would that be? I can't have sudo in my fluxbox startup file at least not that I can see....

Thanks

---

### Post by Xyem on 2008-11-12
gnome-power-manager requiring sudo might have something to do with dbus permissions and the user not being in the right group ( plugdev/powerdev? )

I have a minimal install of 8.10 and I am also trying to get gnome-power-manager to work in Fluxbox. I'll post my findings!

---

