---
title: "[SOLVED] Xfce: Mouse Cursors"
date: 2008-03-21
forum: Desktop Effects &amp; Customization
---

### Post by Bruce M. on 2008-03-21
Hi Folks,

A question for Xfce

I installed a new mouse cursor theme, Grounation, from [Xfce Eye Candy]("http://www.xfce-look.org/content/show.php/Grounation+%28developers+version%29?content=66050") that half works.

I followed these instructions:

```

Cursors (4.4 only)

    * Extract the theme in ~/.icons
          o System wide installation in ${sysprefix}/share/icons
    * Make sure the directory layout looks like this: ./icons/Grounation/cursors
    * Make sure the directory layout looks like this: ./icons/<theme_name>/cursors
    * Select the theme in the Mouse Settings. If there is no tab with cursor themes, make sure xfce-mcs-plugins is compiled with Xcursor support

```

using the ~/.icons because I don't know how to "extract" to: /usr/share/icons I get a "permission denied" ( understandable )

Did a [Ctrl]+[Alt]+[Backspace] - half works.
Did a [Restart] - only half works

Checked the forums and found this:

> 
did you log out and back in?

option #2. set it as the default, so it's everywhere.

gksu mousepad /etc/X11/cursors/core.theme

[Icon Theme]
#Inherits=core
Inherits=Grounation


Did that and again ...
Did a [Ctrl]+[Alt]+[Backspace] - half works.
Did a [Restart] - only half works

It only shows up when running "some" programs, it's here in Firefox.

However if I move the mouse pointer to the title bar of Firefox, either panel or the desktop, it goes back to the default little white cursor.

How can I extract this to: /usr/share/icons to see if that works?

Or is there something else I'm missing?

Thanks
Bruce

---

### Post by cardinals_fan on 2008-03-22
I had a problem like this a while ago, but it eventually went away.  Sorry I can't be more helpful.

---

### Post by kerry_s on 2008-03-22
to put it in /usr/share/icons, launch thunar as root
press> alt+f2
type> gksudo thunar /
then just drag & drop the theme


you probably want to put some right click actions, so it's faster in the future.

for root thunar> gksudo thunar %d
for root mousepad> gksudo mousepad %f

then you can right click a file or folder and launch root

also try rebooting, sometimes the old stuff is cached in memory and doesn't fully get replaced by the theme.

---

### Post by Bruce M. on 2008-03-23
> **kerry_s said:**
> to put it in /usr/share/icons, launch thunar as root
press> alt+f2
type> gksudo thunar /
then just drag & drop the theme


you probably want to put some right click actions, so it's faster in the future.

for root thunar> gksudo thunar %d
for root mousepad> gksudo mousepad %f

then you can right click a file or folder and launch root

also try rebooting, sometimes the old stuff is cached in memory and doesn't fully get replaced by the theme.

Will try this later today.
It's Easter Sunday, have lots to do.
Happy Easter
Bruce

---

### Post by mali2297 on 2008-03-23
I think it would be safest not to install it system-wide right away. Instead, try this approach...

Make a directory **~/.icons/default**,
```

mkdir ~/.icons/default

```
Open a new file **index.theme**,
```

mousepad ~/.icons/default/index.theme

```
Add these two lines to the file:
```

[Icon Theme]
Inherits=Grounation

```
Save, quit and restart X.

---

### Post by Bruce M. on 2008-03-23
> **mali2297 said:**
> I think it would be safest not to install it system-wide right away. Instead, try this approach...

Make a directory **~/.icons/default**,
```

mkdir ~/.icons/default

```
Open a new file **index.theme**,
```

mousepad ~/.icons/default/index.theme

```
Add these two lines to the file:
```

[Icon Theme]
Inherits=Grounation

```
Save, quit and restart X.

At first I thought, perfect this works. Desktop, Panels and Firefox.

But once Firefox was fully loaded, the cursor went back to the default theme.
Slide the pointer to the "hearder", panels and desktop and Grounation takes over.

Seems to be the opposite of my original post.
Hmmmm, must try system wide now.

Be right back
Bruce

[SIZE="4"]**[COLOR="Red"][CENTER]EDIT[/CENTER][/COLOR]**[/SIZE]

I stand corrected.

[Ctrl]+[Alt]+[Delete] resulted in the above.
Did a [Restart] and got the same results
Checked Applications > Settings > Mouse Settings and found it was set to the original, changed that to Grounation and it works everywhere now.

**Thank You mali2297**

Bruce

---

### Post by mali2297 on 2008-03-23
Still another approach...

Open (create if necessary) the file **~/.Xdefaults** and add the line:
```

Xcursor*theme: Grounation

```

---

### Post by Bruce M. on 2008-03-23
> **kerry_s said:**
> to put it in /usr/share/icons, launch thunar as root
press> alt+f2
type> gksudo thunar /
then just drag & drop the theme


you probably want to put some right click actions, so it's faster in the future.

for root thunar> gksudo thunar %d
for root mousepad> gksudo mousepad %f

then you can right click a file or folder and launch root

also try rebooting, sometimes the old stuff is cached in memory and doesn't fully get replaced by the theme.

I do appreciate your response and will keep the info here for future reference.

Especially the %d and %f stuff.  :)
**Thank You kerry_s**

Have a Great Day
Bruce

---

### Post by Bruce M. on 2008-03-23
> **mali2297 said:**
> Still another approach...

Open (create if necessary) the file **~/.Xdefaults** and add the line:
```

Xcursor*theme: Grounation

```

Only goes to show there are more ways to do the same thing.  :)
Thanks for this too.

Have a Great Day
Bruce

---

