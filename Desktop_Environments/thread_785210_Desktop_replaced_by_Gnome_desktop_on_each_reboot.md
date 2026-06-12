---
title: "Desktop replaced by Gnome desktop on each reboot"
date: 2008-05-07
forum: Desktop Environments
---

### Post by DaVince21 on 2008-05-07
Hello,

I seem to be having a problem with Xfce: Xfce runs just fine and fast, however, each time I start it it shows the Xfce desktop for a short while, then switches to the Gnome desktop... I have to enter the Xfce desktop settings and enable "Allow Xfce to manage the desktop" manually each time, which is quite annoying.

It also switches back to the Gnome desktop inbetween using programs sometimes, for example when I try to set an icon theme in Xfce's User Interface Preferences.

Saving the session doesn't work and rather creates duplicate entries of all programs already running that would also start on startup (what a messy mistake by Xfce)... Also, I'm using regular Ubuntu (upgraded 7.04 > 7.10 > 8.04) and used Gnome before I decided to switch to Xfce.

Any help?

EDIT: by the way, it wasn't always like this. It happened sometime after I was messing around with the look/layout preferences and ran the Gnome layout preferences inside Xfce once... This might have messed up something, but I'm not sure what.

---

### Post by mali2297 on 2008-05-07
Hello.

My guess is that the problem lies in one of the hidden configuration files in your home folder (their names start with a dot). To troubleshoot, you could move all those files and directories to a backup folder, then move them back one at a time. Most settings for xfce are in .config, whereas gnome settings are in .gconf and elsewhere. An alternative is to simply start fresh with new configurations for everything.

---

### Post by DaVince21 on 2008-05-07
I found a lot of settings in ~/.config/xfce4 already, but nothing that seems to be pointing towards "launch the Gnome desktop". Can I safely remove these config files (as in, it would regenerate defaults when I restart xfce)? Same question for Gnome settings...

---

### Post by Archmage on 2008-05-07
Are you sure that you set your session to XFC before loggin in?

---

### Post by DaVince21 on 2008-05-07
Of course. I'm absolutely certain it's Xfce that's starting. I'm not really new with Linux, just not too experienced with Xfce's and Gnome's configuration files.

I'll mess around with the configuration files a bit and see what works, thanks for giving me the appropiate locations of the configuration files.

---

### Post by mali2297 on 2008-05-07
> **DaVince21 said:**
> I found a lot of settings in ~/.config/xfce4 already, but nothing that seems to be pointing towards "launch the Gnome desktop". Can I safely remove these config files (as in, it would regenerate defaults when I restart xfce)? Same question for Gnome settings...

Yes, the defaults should be regenerated.

---

### Post by mali2297 on 2008-05-07
> **DaVince21 said:**
> 
I'll mess around with the configuration files a bit and see what works, thanks for giving me the appropiate locations of the configuration files.

You might also want (re)move the **.cache** folder, xfce stores old sessions there.

---

### Post by DaVince21 on 2008-05-07
> **mali2297 said:**
> You might also want (re)move the **.cache** folder, xfce stores old sessions there.
Haaa, this immensely helps since it cleans up the mess that Xfce session saving made! Thanks once again. :)

EDIT: after removing most Xfce configuration files everything works smooth again. No more Gnome desktop, quicker startup!

---

### Post by DaVince21 on 2008-05-17
Just a little note to help other people out there. :)

The problem started appearing again, and then I found out that it was actually only doing that whenever Nautilus started... With some fiddling in the Gnome configuration editor (the one that looks like WIndows' registry editor, with keys and stuff) I managed to turn off an option that would let Nautilus take over the desktop. I'm never seeing it again now! :)

---

### Post by denham2010 on 2008-05-20
Hi,

I was thinking you may have been using Nautilus. I have always found it odd with Gnome that the file manager is tied to desktop management.

Something else you may try, to avoid any future problems, would be to use Thunar (this is the XFCE file manager). Or if you prefer to use Nautilus over Thunar, change the launcher for Nautilus to add the option --nodesktop. This option will stop Nautilus trying to take control of the desktop when launched.

Cheers.

---

### Post by DaVince21 on 2008-05-21
Actually, I recently switched to XUbuntu and when the problem started reappearing I did the above trick again. I don't really like Thunar because I'm used to Nautilus' extendability that I wouldn't want to lose (SVN scripts, open as admin, create archive, open terminal here...).

---

### Post by mali2297 on 2008-05-21
> **DaVince21 said:**
> Actually, I recently switched to XUbuntu and when the problem started reappearing I did the above trick again. I don't really like Thunar because I'm used to Nautilus' extendability that I wouldn't want to lose (SVN scripts, open as admin, create archive, open terminal here...).

I would say that those features can be obtained in Thunar through *custom actions*, see
[http://thunar.xfce.org/pwiki/documentation/custom_actions](http://thunar.xfce.org/pwiki/documentation/custom_actions)

I find Thunar to be the best part of Xfce. Of course, you're free to use whatever file manager that you're comfortable with. Xfce aims to be modular and thus allow the user to pick the pieces s/he wants.

---

