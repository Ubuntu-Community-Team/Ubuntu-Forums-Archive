---
title: "Blacked out boxes in Audacity window under Gnome after upgrade 18.04 to 20.04"
date: 2021-09-05
forum: Desktop Environments
---

### Post by AR_Kozz on 2021-09-05
Audacity installed under 18.04 became inoperable after upgrade from Ubuntu 18.04 to 20.04. Not sure what Audacity version was then, now it's 2.3.3. GNOME Shell 3.36.9 on xorg, GTK 3.24.20

It starts with the level meters and tracks window blacked in. The tracks window updates and shows its contents if the app window edge is grabbed and moved by the mouse pointer. It doesn't show anything new until the edge is grabbed and moved again. 

[IMG]https://drive.google.com/file/d/19GoJIf-gen9Ida_0UKiM9crxdTXOXIms/view?usp=sharing[/IMG]
[IMG]https://drive.google.com/file/d/15xwBAC46DL1G-1kHKE8z_cCOE7PJY5gs/view?usp=sharing[/IMG]
[IMG]https://drive.google.com/file/d/17uLoJ8SUCQXcE6ea4kjD6dgs0zFLrq2n/view?usp=sharing[/IMG]

This doesn't happen with any other programs, but it also doesn't happen when I run as another user or as root. Some configuration in my home folder, then. I've looked around and tweaked what I could with Tweaks and dconf-editor no effect. What would be responsible for this part of an app window's display?

---

### Post by Dennis N on 2021-09-06
I did the same upgrade from 18.04 to 20.04, but don't see what you describe. It sounds unusable. I suggest first trying a different application theme. If you don't find or get a fix, you might try a different Audacity package like snap, flatpak, or appimage. All of these types are available and should be packaged to give a usable interface. They are also the current version (3.2 I think). 

The Audacity web site offers a download only as an Appimage. Appimages are simple to start using without much effort.

---

### Post by AR_Kozz on 2021-09-07
Thanks, but I can rule out a problem with audacity as installed because it works fine as root (bypassing my home config) and as a new, OOTB default alternate user I created to test it. Importing the audacity config files from those to my home folder doesn't make it work under my normal login. So there's something else in there causing it to behave differently than for the alt-user.  

Question here is, what are the "usual suspects" for an application window glitching this way? I have tried theme switches, but it made no difference. I'll try switching every setting to what the alt-user has.

---

### Post by guiverc on 2021-09-07
Working as 'root' I think a huge clue as to your issue.

I've recently done a 18.04 to 20.04 upgrade, and had no issues.

A GUI tool should not be run as root; but your mention of it implies to me you've done it before, probably made a change (*and thus changed ownership to a file; config or otherwise*) to 'root', meaning the default user no longer can access that file - causing the issue that you describe, but that won't impact the program when run as root (*or other users who have different config files owned by the respective users*)..

I'd check for ownership of files used by audacity in the username you have issue for, are any files in your $HOME owned by root; because you changed a setting whilst using elevated privileges.

I don't know that this is your issue; but it what screams out from your description in my opinion.  (*you need to explore files themselves with `nautilus` or command line*)

---

### Post by AR_Kozz on 2021-09-07
Nope, I didn't run a gui as root before the issue started. As I said, it started after the upgrade. I sudo'd it diagnostically, and it ran with the welcome splash, used no configs or plugins from /home, and defaulted saves to root-owned folders. Tried chown -R self on /home anyhow and issue persists. 

meanwhile I've also tried swapping the gnome related configs (gnome-shell, gtk, deconf, nemo) from the sub-user's folder to /home, to no effect; and commented out all other gnome-related stuff in /home that wasn't in the sub-user's folder, still no effect. 

Watching system monitor, I see xorg's cpu use jump when I mouse-grab and move the audacity window edge. So I'm leaning toward gnome being exonerated and it's an X issue. Not sure if this or another forum is the appropriate place for that. 

I may be consigned to using Audacity as my sub-user, unfortunately.

---

### Post by ActionParsnip on 2021-09-07
if you make a fresh Ubuntu user and use that, rather than root. Is it the same. If yes then its a permission thing (as root works OK) if not then I suspect its the config folder for Audacity with some setting it doesn't like or a desktop  theme issue

---

### Post by AR_Kozz on 2021-09-07
As I already mentioned twice, it does work on a sub-user I created for diagnostics. Importing the configs and themes from there doesn't fix. Nothing in /home is owned by root or another user.

These images show Audacity 1) when started 2) after recording something 3) after moving the window edge and the recorded waveform appears. I'm hoping someone knows what layers of the OS are responsible for displaying these subwindows and could be glitching. 

[https://drive.google.com/file/d/19GoJIf-gen9Ida_0UKiM9crxdTXOXIms/view?usp=sharing]("https://drive.google.com/file/d/19GoJIf-gen9Ida_0UKiM9crxdTXOXIms/view?usp=sharing")

[https://drive.google.com/file/d/15xwBAC46DL1G-1kHKE8z_cCOE7PJY5gs/view?usp=sharing]("https://drive.google.com/file/d/15xwBAC46DL1G-1kHKE8z_cCOE7PJY5gs/view?usp=sharing")

[https://drive.google.com/file/d/17uLoJ8SUCQXcE6ea4kjD6dgs0zFLrq2n/view?usp=sharing]("https://drive.google.com/file/d/17uLoJ8SUCQXcE6ea4kjD6dgs0zFLrq2n/view?usp=sharing")

---

### Post by Dennis N on 2021-09-07
Out of curiosity, I downloaded and tested the Appimage of Audacity with a test recording. Works beautifully. Screenshot attached (Version 3.0.4 running on Xubuntu 20.04). Everything is clear and readable.

---

### Post by ajgreeny on 2021-09-07
I think this may be a known bug with problems related to GTK3 and Audacity's use of wxGTK which is something I saw in the past with the same problem you now have.

I can't remember how I solved this but my memory points to an edited command in its desktop launcher file. I will look tomorrow when back on my Xubuntu system; I think I have a record of this in a text file on that machine.

---

### Post by ajgreeny on 2021-09-08
OK, this does seem to be a wxGTK problem and I did used to have to start Audacity in 18.04 using the command ```
bash -c "GTK_IM_MODULE=; audacity %F"
``` in the desktop launcher file.

It may be that updates to the versions of various libwxgtk and wxwidgets packages have overcome this, and I always use a clean install of ther OS, now 20.04, not an upgrade, and also with Xubuntu, ie, Xfce4 not gnome.

Try that start command to see if it works for you; make sure you don't miss the " " in that command or it will certainly fail.

---

### Post by AR_Kozz on 2021-09-11
Success. Thanks. It works with message "%F could not be found It has been removed from the list of recent files."

Not sure what the gtk issue is, and don't wanna know as long as this fix keeps working.

---

### Post by ajgreeny on 2021-09-12
Ah!

That ***%F*** is simply the suffix added to commands in .desktop launcher files; if you use the command in terminal you can cut the %F from the command used and it should work fine.

---

