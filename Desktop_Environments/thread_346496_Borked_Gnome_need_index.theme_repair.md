---
title: "Borked Gnome: need index.theme repair"
date: 2007-01-25
forum: Desktop Environments
---

### Post by ubu fubar on 2007-01-25
Hi all,

I've broken my Gnome desktop :(

I installed comixcursors through Synaptic, then chose the small orange set (name forgotten) as my cursor theme under mouse preferences. This worked well, but when trying to select a Gnome theme to suit the cursor color I was surprised to see the comixcursor sets listed under the available icon themes. wtf?? I was under the assumption that comixcursor provided only a set of replacement cursors, not other theme elements.

Anyway this surprise, coupled with an overly sensitive laptop touch pad, led me to select a comixcursor icon theme. Now, there are 2 things to note here:

1. the theme select dialog doesn't require you to click the OK button before it's applied, in order to give you a preview of the theme before finally applying. Changes are immediate.

2. the comixcursor set does not supply an icon theme.

The net result was a warning that certain theme directories don't exist, and a complete and instantaneous disappearance of *all* GUI elements. Not even an [ok] [cancel] option on the warning.

Fortunately, I still had a couple of app windows and a term open, so I could type gedit and get a text editor window, and open firefox to post this wail. But any attempt to reopen a Gnome based window would fail with the error about not being able to "find the comix-cursor.theme" or something.

Other accounts on this machine work ok (as should be expected), but mine is borked. Logging in with gnome-default or failsafe is no use, as they don't run startup scripts, and any changes I make in gnome conf editor don't stick.

So I figured I need to find my theme config file, and reset the icon theme. Grepping for "comix" through my dotfiles brings up .themes/me/index.theme, where I've tried numerous variations of IconTheme=foo settings. Before this escapade, I was running the White Glass cursor theme, but I've tried:

IconTheme=whiteglass
IconTheme=WhiteGlass
IconTheme=Whiteglass
IconTheme=White-Glass

and probably many more, but at this stage I no longer care about bloody cursor themes. How do I reset this setting to a default Gnome setting so I get my interface back?

Yours GUIless,

---

### Post by Ptero-4 on 2007-01-25
delete your whole .gnome2 dir and any other dotdir that might be related to gnome. Then log off and back on, gnome should just recreate them off the system defaults.

---

### Post by ubu fubar on 2007-01-26
Yeah, that worked. Cheers!

Of course, I lost all the customisations I'd made previously. But dragging the trashed dotfiles and folders back into my home folder recreated everything as before.

I left my old .theme in the trash however, and removed comixcursor through synaptic.

I'd previously tried logging off and back on again with just my .theme trashed, it seems strange that didn't work and required trashing everything .gnome...

---

### Post by ComplexNumber on 2007-01-26
**ubu fubar**
all you had to do was log out and then back in again. the system would have reverted to the way it was before you changed it to the comix cursors.

---

### Post by ubu fubar on 2007-01-26
> **ComplexNumber said:**
> **ubu fubar**
all you had to do was log out and then back in again. the system would have reverted to the way it was before you changed it to the comix cursors.

Nope, that's the first thing I tried - it logged in with no GUI, just a term window full of theme errors. I even tried restarting the machine to no avail.

The only way I could bring up a Gnome desktop was by logging in with the failsafe Gnome session.

---

### Post by ComplexNumber on 2007-01-26
> **ubu fubar said:**
> Nope, that's the first thing I tried - it logged in with no GUI, just a term window full of theme errors. I even tried restarting the machine to no avail.

The only way I could bring up a Gnome desktop was by logging in with the failsafe Gnome session.
someone else had EXACTLY the same problem as you because i answered their problem about a week ago. they asked for a way to change the icon theme because they clicked on one of the cursor themes by mistake and all their icons went, leaving the desktop unusable. i told them where to find where the icons info is held in .gconf, but they told me that it wasn't necessary afterall because they just had to logout and then back in again. so i replicated it....and yes, it was solved by logging out and then back in again. 

you see, the thing is,  the system always rolls back to the previous state if a corrupted icon set is chosen. therefore, there must be something else that must have gone wrong in your case that you may not have picked up on.

---

### Post by Tsen on 2007-01-27
I had a very similar problem.  It might have been the comix cursor, too, incidentally--I don't remember.
I was installing themes and cursors and looking for a theme that would suit my desktop.  While arrowing down through the themes to preview them all, I saw one (possibly comix) that I'd installed but thought was only a cursor, not a theme.  Curiousity killed the cat.  Anyway, same problem happened to me.  Left my desktop totally unusable.
I rebooted, but Ubuntu freezes on startup, probably because I enabled auto-login and everytime it tries to load up Gnome it freezes on me.
I'm booting off of a live CD right now, but I have access to the safe mode command prompt if I boot normally.
Is there any way I could do what Ubu Fubar did, and how would I go about doing that in layman's terms? (I'm rather new to Linux)

---

### Post by ubu fubar on 2007-01-27
Here's what worked for me:

Log in using the gnome failsafe session or your live cd, and navigate to your home directory using Nautilus. Hit control + h to show your hidden dotfiles, then trash (not delete) the following hidden directories:

.gnome
.gnome2
.gconf
.themes

Ensure these files are moved to the .trash directory in your home folder - I'm guessing that if you use the live cd they might get moved to another .trash?

Now log in again using your default session, and your desktop should be in the default Gnome state. Gnome will recreate these folders in your home dir automatically.

To restore any customisations you've previously made to your profile, simply drag the trashed folders back into your home folder, overwriting the defaults. Do NOT restore your .themes folder, simply reconfigure your theme using System -> Preferences -> Theme.

---

### Post by Tsen on 2007-01-30
Alright, everything's working again.  Thanks!

---

