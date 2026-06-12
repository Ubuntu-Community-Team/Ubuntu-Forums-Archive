---
title: "Ubuntu 11.10  Gnome panel (repeated) looking very strange"
date: 2011-10-14
forum: Desktop Environments
---

### Post by hamid.afshar on 2011-10-14
Hi guys,

I just downloaded the new Ubuntu 11.10.

And my gnome panel has gone mad. I have got an attachment of what this looks like. I have been reading around for ages but cant find the solution to my problem.

Please HEEEELLLLLPPPPPP as I am very needy!!!!!!   :confused:

---

### Post by hamid.afshar on 2011-10-14
if i go to terminal and type gnome-panel i get this:

(gnome-panel:2522): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2295: signal `size_request' is invalid for instance `0x1c04e10'

---

### Post by woodyg on 2011-10-14
Same problem here I think. In 11.04 it worked great, now something is not quite right... :(

---

### Post by randywilharm on 2011-10-14
Is'nt that the Unity panel?

---

### Post by collisionystm on 2011-10-14
you cannot run gnome-panel in 11.10. remove it.

You must run gnome-shell. You can see it at gnome.org.

---

### Post by Copper Bezel on 2011-10-15
Or gnome-session-fallback, which includes a port of the Gnome Panel to GTK3. (Since it's a little-known yet often-suggested feature of the new panel, I'll also say, you now need to hold Alt while clicking to modify things.)

---

### Post by zeropointer on 2011-10-23
I was getting a similar problem:

(gnome-panel:2160): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2295: signal `size_request' is invalid for instance `0xcddac0'

I tried removing gnome-panels, and gnome-shell, however when you install gnome-shell you get gnome-panel.
I thought it was graphics driver but it wasn't.

If you log in as guest, gnome-shell works. (I was using Gnome without effects)
Gnome shell default settings work. Therefore, it has to do with the settings. Also, I remembered I was configuring the gnome panels when the gnome shell started to crash.

This is what fixed it for me:

Go into terminal
```
cd ~/.config/dconf

mv user use

```Log out or reboot. (I rebooted, lightDM problems)

By renaming the user settings you make a backup at the same time.
This just resets the gnome-shell settings and this worked for me. It took me a while to figure out where Gnome 3 settings were kept.

I hope that helps.

---

### Post by hamid.afshar on 2012-02-09
Well,

This is not exactly a fix to the problem but just when you are about to click on the user and enter your password on Ubuntu 11.10, there is a set of options which allows you to choose which mode of Ubuntu you want to log in to. 

The list consists of:

.Gnome
.Gnome (classic)
.Ubuntu
etc....

Pick each and see which one works for you. 

This will fix your problem. :popcorn:

---

### Post by betterhands on 2012-06-24
> **zeropointer said:**
> 
This is what fixed it for me:

Go into terminal
```
cd ~/.config/dconf

mv user use

```Log out or reboot. (I rebooted, lightDM problems)

By renaming the user settings you make a backup at the same time.
This just resets the gnome-shell settings and this worked for me. It took me a while to figure out where Gnome 3 settings were kept.

I hope that helps.

thanks--this worked for me as well withe the same issue in 12.04.

---

### Post by JoZ3 on 2013-04-25
> **zeropointer said:**
> I was getting a similar problem:

(gnome-panel:2160): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2295: signal `size_request' is invalid for instance `0xcddac0'

I tried removing gnome-panels, and gnome-shell, however when you install gnome-shell you get gnome-panel.
I thought it was graphics driver but it wasn't.

If you log in as guest, gnome-shell works. (I was using Gnome without effects)
Gnome shell default settings work. Therefore, it has to do with the settings. Also, I remembered I was configuring the gnome panels when the gnome shell started to crash.

This is what fixed it for me:

Go into terminal
```
cd ~/.config/dconf

mv user use

```Log out or reboot. (I rebooted, lightDM problems)

By renaming the user settings you make a backup at the same time.
This just resets the gnome-shell settings and this worked for me. It took me a while to figure out where Gnome 3 settings were kept.

I hope that helps.

Thanks so much, work fine in my ubuntu 13.04 (upgrade from 12.10).

---

