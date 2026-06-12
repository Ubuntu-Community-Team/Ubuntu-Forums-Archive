---
title: "Wrong title colours in Unity"
date: 2011-04-29
forum: Desktop Environments
---

### Post by jttj on 2011-04-29
Hi there,

Sorry if this question has already been asked; I did have a good hunt around before.

Just upgraded from 10.10 to 11.04. The upgrade took hours and in the end wasn't able to take across my existing applications. Fair enough, I don't mind too much.

However, although everything works fine, i'm left with a bit of an odd colour situation on the top panel of Unity. The application title/menu bar, along with the clock on the top panel, is set to a text colour of black - which is pretty illegible on the dark background.

There doesnt seem to be any obvious settings anywhere for this - the normal Appearance settings do not affect this (set to the default "New Wave"), and i cannot find any other relevant settings in the GUI.

Please see the attached image.

Many thanks for any suggestions you can make.

---

### Post by pauljwells on 2011-04-29
Looks odd!
What happens if you set up a new user and log in as them? If that looks ok then it's a config file in your /~ directory - switch on 'show hidden files' in nautilus preferences to see the config files

---

### Post by jttj on 2011-04-29
Thanks for the pointer... I tried creating a new user, and it works OK.

Tried deleting a few hidden settings folders in my user profile, and haven't got it yet.

I could just use a new profile instead, though i'd need to copy over my files and some settings for a few other applications (which I have to get around to reinstalling at some point... sigh)

Yeah, unless anyone knows the specific setting for this, i'll probably do that.

---

### Post by Krytarik on 2011-04-29
Do you have a file called ".gtkrc-2.0" in your home directory?
If so, that may hold the wrong setting.

---

### Post by jttj on 2011-04-29
> **Krytarik said:**
> Do you have a file called ".gtkrc-2.0" in your home directory?
If so, that may hold the wrong setting.

Nope sorry, I don't seem to have that one anywhere.
I deleted .gnome2, .nautilus, .compiz, and a few others I can't remember (possibly .unity if that exists?)

---

### Post by Krytarik on 2011-04-29
> **jttj said:**
> Nope sorry, I don't seem to have that one anywhere.
Sorry, I wasn't very accurate, it would have been at the toplevel of your home directory, "~/.gtkrc-2.0".

I wouldn have done exactly what you did now, but hopefully it will fix it.

---

### Post by jttj on 2011-04-30
Sorry guys, seem to have fixed it now. I changed my colour scheme to Ambiance and that works fine. I think that's meant to be the default anyway?

I guess it tried to copy my old colour scheme but screwed it up in the process.

Many thanks for the help.

---

### Post by Krytarik on 2011-04-30
> **jttj said:**
> I think that's meant to be the default anyway?
Yeah, that's the default.

Glad that you sorted it.

---

