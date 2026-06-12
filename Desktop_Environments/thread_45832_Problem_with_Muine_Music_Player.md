---
title: "Problem with Muine Music Player"
date: 2005-07-01
forum: Desktop Environments
---

### Post by Ginger on 2005-07-01
First, I should preface this with a warning... I'm a bit new to this. I don't understand a lot of what's being said on the forums, but I'm trying to learn more about Linux, so please be patient with me and spoonfeed me any advice you have. Basically, assume that I know very little :o)

I got Linux (Gnome, Ubuntu) a few weeks ago. It has been working perfectly. But today, I closed Muine Music Player and tried to reopen it about a half hour later and the computer said it was loading, but then the cursor just went back to being an arrow and Muine never loaded.  
I decided to shut the computer down and log in again.  This made no difference.
When I tried to access it through the terminal, I got this message:

(muine:16325): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Failed to export D-Bus object: No reply within specified time

Then the Muine window popped up, but it was blank, with none of the music I had previously imported into it. It would allow me to import music, but when I tried to play a song, the Muine window just disappeared.
 I obviously have no idea what the terminal message meant, since I'm quite new to this, but I was hoping that someone else could guide me in the right direction to fixing this, because I like Muine.
Also, I tried uninstalling and reinstalling, to no avail. 
Any advice would be greatly appreciated. Thanks!


Additional note... after I imported songs into the player and picked an album to listen to, I hit play and the window closed, but the terminal gave me this message:

(muine:16491): Gtk-CRITICAL **: gtk_tree_view_scroll_to_cell: assertion `tree_view->priv->tree != NULL' failed
Segmentation fault


Thoughts? Advice?

---

### Post by srt4play on 2005-07-02
Never heard of Muine, I'll have to check it out.   From what you stated it looks like Muine is crashing (segmentation fault).  Uninstall it then reinstall, if it still crashes check to see if there's a newer version available and if you have the latest version maybe go back to a previous version and see if that fixes the problem.

---

