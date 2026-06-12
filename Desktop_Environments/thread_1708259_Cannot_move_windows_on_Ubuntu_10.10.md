---
title: "Cannot move windows on Ubuntu 10.10"
date: 2011-03-16
forum: Desktop Environments
---

### Post by paulmerton on 2011-03-16
Hi, I'm relatively new to using Linux, so forgive me if this seems easy to fix, but I just don't know where to begin:

I'm running Ubunutu 10.10 (64-bit) and used the Synaptic package manager to install CompizConfig Settings Manager a few months ago, thus enabling lots of shiny window manager effects. I haven't touched these settings for months, but within the last few weeks I have noticed that I can no longer reposition any windows. This may have happened after applying some updates.

I can still maximise and minimise windows, but I cannot move any of them - dragging the title bar has no effect whatsoever. 

How can I make my windows movable once more?

---

### Post by paulmerton on 2011-03-16
I've also just noticed that I cannot resize any windows (other than maximise/restore/minimise)

---

### Post by Krytarik on 2011-03-16
First, check "~/.xsession-errors" for error messages after trying the mentioned actions.

Then, the following Compiz plugins are able to cause this:
- Wobbly Windows
- Move Windows
- Resize Windows
You may try disabling them to narrow down the issues.

---

### Post by paulmerton on 2011-03-18
> **Krytarik said:**
> First, check "~/.xsession-errors" for error messages after trying the mentioned actions.

Then, the following Compiz plugins are able to cause this:
- Wobbly Windows
- Move Windows
- Resize Windows
You may try disabling them to narrow down the issues.

Thanks for the suggestions.  .xsession-errors contains the following errors:

 /usr/bin/compiz (core) - Error: Couldn't load plugin 'move'
 /usr/bin/compiz (core) - Error: Couldn't load plugin 'resize'

I tried enabling/disabling the Compiz plugins you mentioned, plus restored everything to default settings, but I still get the above errors.

---

### Post by Krytarik on 2011-03-18
Try running those commands, in a terminal:
```
gconftool --recursive-unset /apps/compiz/plugins/move
gconftool --recursive-unset /apps/compiz/plugins/resize
```
Then restart Compiz:
- press Alt+F2
- enter
```
compiz --replace
```

---

### Post by paulmerton on 2011-03-19
That didn't fix it either :(

---

### Post by Krytarik on 2011-03-19
- logout
- switch to a console by pressing Ctrl+Alt+F1
- login there
- remove the directory "~/.compiz"
- *rename* the directory "~/.gconf/apps/compiz"
- switch back to GDM with Ctrl+Alt+F7/F8
- login again

This will reset all your Compiz settings.

If it works after that, try renaming "~/.gconf/apps/compiz" back.

---

### Post by paulmerton on 2011-03-19
Thanks for another suggestion, but that hasn't fixed it either. I still get the same errors appearing in .xsession-errors and can't move/resize windows.

---

### Post by Krytarik on 2011-03-19
Then I assume that the issue also occurs with a fresh user account?!

---

### Post by paulmerton on 2011-03-19
> **Krytarik said:**
> Then I assume that the issue also occurs with a fresh user account?!
Yes - I just created a new user account and I still can't move/resize windows.

---

### Post by Krytarik on 2011-03-19
But disabling those plugins make the actions work, right?
At least as a temporary workaround. I will get back on this later.

---

### Post by paulmerton on 2011-03-19
> **Krytarik said:**
> But disabling those plugins make the actions work, right?
At least as a temporary workaround. I will get back on this later.
No, disabling those plugins had no effect.

However, I have just used the Synaptec package manager to remove every package with compiz in the name, and after rebooting, I can now move and resize windows. That's an improvement, but after reinstalled the CompizConfig Settings Manager and all of its dependencies, it seems that none of the settings have any effect.

It's nice to be able to move windows again, but I miss my Wobbly Windows now! :)

---

### Post by Krytarik on 2011-03-19
OMG, you could have just said: "No, it doesn't work."

And I would have said then:

"Replace it with Metacity:
- press Alt+F2
- enter:
```
metacity --replace
```"
Now that we are here:
Also re-install the package "compiz" and its dependencies.
Since CCSM is apparently not dependend on Compiz itself. :p

---

### Post by Krytarik on 2011-03-26
Does the issue still exist?

Did you re-install the compiz packages?
Maybe that also fixes the issue.

---

### Post by digimancer on 2011-09-14
This may sound like an absolutely lame answer, but after reading this tread and realizing that none of the fixes worked for this guy I decided that maybe it was user error (on my part and his) as I had previously installed "Advanced Desktop Effects Settings (ccsm)" and likely messed something up... Prior to uninstalling it that is...

So after reading all of this and realizing that the "move" and "resize" options are considered "plugins" I decided to reinstall "Advanced Desktop Effects Settings (ccsm)" and poke around... What do you know... The move and resize plugins were both unchecked. I re-checked them and BAM! working again :o

---

