---
title: "[SOLVED] Can't stop Console window from opening during boot."
date: 2008-05-17
forum: Desktop Environments
---

### Post by Phrawm48 on 2008-05-17
For Ubuntu 7.04 (Feisty), Gnome 2.18.1.

I've accidentally done something that causes a Console window to be opened as part of every boot.  The working directory of the Console window is always equal to "/etc" (and the window is always in the second desktop of four...).

I believe I created this unwanted behavior when I tried (and failed) to create a cron / anacron process to periodically run a script.  Now I just want to get whatever I've changed back to its default state.

I've unsuccessfully tried using "crontab -e" (both with and without "sudo" as a prefix) to clean up any changes I made have made to the crontab file.  I've also unsuccessfully tried using the log viewer to more clearly identify what's creating the unwanted Console window during boot.

Can anyone please suggest how I can fix the situation so that I don't have to manually close the console window after every boot?

Cheers & thanks,
Ric
SFO

---

### Post by kshane on 2008-05-17
> **Phrawm48 said:**
> For Ubuntu 7.04 (Feisty), Gnome 2.18.1.

I've accidentally done something that causes a Console window to be opened as part of every boot.  The working directory of the Console window is always equal to "/etc" (and the window is always in the second desktop of four...).

I believe I created this unwanted behavior when I tried (and failed) to create a cron / anacron process to periodically run a script.  Now I just want to get whatever I've changed back to its default state.

I've unsuccessfully tried using "crontab -e" (both with and without "sudo" as a prefix) to clean up any changes I made have made to the crontab file.  I've also unsuccessfully tried using the log viewer to more clearly identify what's creating the unwanted Console window during boot.

Can anyone please suggest how I can fix the situation so that I don't have to manually close the console window after every boot?

Cheers & thanks,
Ric
SFO

This may be a little simplistic, but perhaps you could try just setting the "Remember Currently Running Applications" under Sessions, after shutting down all you don't want running?

Kevin

---

### Post by Phrawm48 on 2008-05-17
K:

Thanks -- that did indeed work.

To expand the solution a bit, I closed all apps and windows (my preferred startup state), chose System > Preferences > Sessions, then chose Session Options to save the session.

Next boot the unwanted window was gone.

Cheers & thanks 'gain,
Ric
SFO

---

