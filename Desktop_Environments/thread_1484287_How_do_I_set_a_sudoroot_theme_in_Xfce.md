---
title: "How do I set a sudo/root theme in Xfce?"
date: 2010-05-15
forum: Desktop Environments
---

### Post by fredbird67 on 2010-05-15
I'm running PC/OS, which is based on Xubuntu, and I've got something rather ambitious I'd like to do here.  Due to a little bug I ran into when installing Shiki-Colors in Synaptic (All the Arc-Colors themes also showed up in the GTK theme list, and they DON'T belong there!), I had to put them all into the /home/userID/.themes directories for each user on here in order to fix that bug.

However, I can't stand that ugly default theme that appears when I'm doing something that requires administrative privileges.  Therefore, I'd like to know if there's a way to make the root user use the Shiki-Wine GTK theme and the GNOME-Wine icon theme?  Better yet, if possible, I'd like to have it do this regardless of whether the theme I'm currently using is found in /usr/share/themes or in my local .themes folder.

I've found a way on here to do this using GNOME, but I don't know how to do this for Xfce, since I would assume that the command involved to open Xfce's theme settings would be different from the one for GNOME'S theme settings.  Any ideas?

Thanx in advance,
Fred in St. Louis

---

### Post by portentum on 2010-05-15
The root home directory is /root, so /root/.themes would be the equivalent for that.

For changing the xfce settings, you can simply sudo xfce4-settings-manager.

Hope this helps.

---

### Post by fredbird67 on 2010-05-15
Well, I tried all that, but I opened Synaptic and still got the ugly "Raleigh" theme and the GNOME default icons.  Oh well, it's not that big a deal -- it was just an idea.  Thanx for trying, though.

---

### Post by portentum on 2010-05-16
Hmmm.. I'm downloading a PC/OS iso right now to play with this some, as default behavior on my Debian system and the Xubuntu live disc I just ran is to use the user theme for applications run as root. 

If I understood your problem correctly applications you sudo are not using your user theme, which is located both in ~/.themes and /root/.themes? The only problem I could find was an old Ubuntu bug report saying it wouldn't use a theme if it was only located in ~/.themes. Hmmm. 

I was 100MB into a PC Linux OS download before I realized PC/OS was actually a distro and not shorthand. :oops: 

Hopefully we'll get this figured out, I'm interested in what's going on.

edit: Do you have a /root/.gtkrc-2.0 file? If not, does creating one with the desired settings help?

Example settings:
```
gtk-theme-name="Shiki-Wine"
gtk-icon-theme-name="gnome-wine"
```

edit2: Well, I'm stumped.
After downloading a PC/OS live disc, I've successfully switched the root theme. I did it using the same instructions above. :s
I copied the ~/.themes and ~/.icons folders to /root/, then used sudo xfce4-settings-manager to set the theme and icon sets. Synaptic and other applications run as root then had the proper themes when run under a normal user account.

---

