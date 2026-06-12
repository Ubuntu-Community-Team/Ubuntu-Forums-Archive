---
title: "Configuring Notifications"
date: 2009-04-25
forum: General Help
---

### Post by daz4126 on 2009-04-25
The new notifications system is nice, but are you able to configure them - how they look, where and when they appear?

DAZ

---

### Post by soro2005 on 2009-04-25
I think the answer is "No." It's meant to not even have you think about how you would like to have it. At some point, it'll probably be themeable.

---

### Post by spiderbatdad on 2009-04-25
if you open the main menu under System > Preferences, then select System Preferences on the left side of the main menu screen, pop-up notifications will be listed on the right, just above power management. Check the box to add the item to System > Preferences menu. There doesn't seem to be much to it yet...as a feature. For example no matter what I select, the notifications always appear in the top right. I didn't try the standard theme...Those are the only two configurable aspects I saw...other than to disable all together.

---

### Post by daz4126 on 2009-04-26
That's strange - I don't have that option in my menu at all. There are some keys listed in the Configuration Editor. Hopefully it will be themeable soon - the black background doesn't quite fit in with my desktop.

DAZ

---

### Post by spiderbatdad on 2009-04-26
you dont have which, the main menu or pop-up notifications?

---

### Post by daz4126 on 2009-04-26
The option to choose pop-up notifications (second picture)

DAZ

---

### Post by Mrmental on 2009-04-26
As far as I can tell, this has been completely removed from the release version of Jaunty; it doesn't appear, activated or deactivated in Alacarte.

As the immortal Pepe le Pew might say: 'Le sigh'

I think this might have gone the way of screensaver preferences, which were removed because one of the great grey eminences at Gnome decided that changing them was too much for my feeble end-user brain to handle.

This was because it was decided that screensaver customisation was a useless option, and thus didn't gel with Gnome's stated goal of simplicity.

I appreciate simplicity, I really do, and it's a laudable goal in a Desktop Environment. But surely the point of simplicity in a computing environment is that it doesn't get in your way while you're trying to use it.

Here, we're talking about a feature that would let you control the things that pop up on your screen and get in your way, which has been removed in the name of simplicity.

Once again, in the manner of the inimitable Monsieur Le Pew: 'Le sigh.'

Not trying to flame here.(That said, some fallout from an afternoon's frustrating inability to get pidgin notifications to pop up on screen for only a second may creep in.)
I'm just saying that if this was the logic by which this feature was removed, it was a silly, muddle-headed logic.
Also, if anybody can point me in the direction of a .deb file for this phantom daemon customiser, I would be eternally greatful. Well,not eternally greatful, but I think I could manage at least fortnight.

---

### Post by binbash on 2009-04-26
> **daz4126 said:**
> The option to choose pop-up notifications (second picture)

DAZ

It is removed at final release.It was there at alpha tho

---

### Post by spiderbatdad on 2009-04-26
> **Mrmental said:**
> 

Not trying to flame here.(That said, some fallout from an afternoon's frustrating inability to get pidgin notifications to pop up on screen for only a second may creep in.)


Have you looked into the plugin listed in pidgin tools called libnotify-popups?

---

### Post by umaxtu on 2009-04-26
> **spiderbatdad said:**
> Have you looked into the plugin listed in pidgin tools called libnotify-popups?

where is this plugin?

---

### Post by spiderbatdad on 2009-04-26
here:

---

### Post by soro2005 on 2009-04-26
It's a seperate package. You have to install pidgin-libnotify. Then you'll have the plugin in the list.

---

### Post by spiderbatdad on 2009-04-26
ah thanks for clarifying that. apparently forgot that step.
```
sudo apt-get install pidgin-libnotify
```
Then find the plugin under the tools>>plugins menu.

---

### Post by Mac181 on 2009-04-30
Fantastic. It appears that unchecking the libnotify popups in the tools->plugins menu of pidgin disables the annoying popup notifications whenever a buddy signs in. :)

---

