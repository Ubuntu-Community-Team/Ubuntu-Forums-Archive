---
title: "kde-gnome mixture problem"
date: 2005-06-11
forum: Desktop Environments
---

### Post by freelsjd on 2005-06-11
I installed the standard ubuntu, then install kubuntu on top of that. This way, I can request either gnome or kde from a kdm login screen and use either one...part of the advantage of linux, I have a choice !

Well, some of the applications such as evolution or even firefox, are tied to the gnome desktop setup such that if I specify a background wallpaper screen in gnome, it bleeds over into kde when I login under kde. How can I eliminate that ?

---

### Post by royg1234 on 2005-06-28
I am getting the same problem, except the other way around, and das ist nicht gud.

---

### Post by royg1234 on 2005-06-28
actually, things like Synaptic seem to follow my gnome theme, but most of the rest of the desktop doesn't.

---

### Post by royg1234 on 2005-06-28
and I've uninstalled these packages, followed by a ctrl+alt+backspace, but still no dice.

[list]
[*]gtk2-engines-gtk-qt
[*]gtk2-engines-qtpixmap
[*]gtk-engines-qtpixmap
[/list]

by the way, I think these are the packages that make Firefox look pretty in KDE.  Just go to the KDE kontrol center > appearance.

---

### Post by Xian on 2005-06-28
[QUOTE=freelsjd]Well, some of the applications such as evolution or even firefox, are tied to the gnome desktop setup such that if I specify a background wallpaper screen in gnome, it bleeds over into kde when I login under kde. How can I eliminate that ?[/QUOTE]
I don't use those programs so I can't confirm this issue, but have you considered changing the desktop path in KDE? I'm just thinking that if you separate it entirely from Gnome then you won't have any "bleed over" effects. 

If you want to try this just open the KDE Control Center and goto:
System Administration > Paths

In that window you will see a line that says 'Desktop Path'.
Change that to something like /home/username/kDesktop

Then when you click to Apply it will ask if you want to move your files.
Confirm this and let KDE transfer those over to the new path.

Then you'll need to open konqueror and make a new folder in your /home directory called 'Desktop'. This will be for Gnome since it is unaware that you have gone about changing the paths. Also, this will effectively partition the Gnome and KDE desktops from each other, allowing them to operate independently.

---

### Post by mknepher on 2005-06-29
Are you running/launching nautilus under KDE? The GNOME background is actually just the background image for the $USER/Desktop folder in nautilus, and launching nautilus without the --no-desktop switch will result in the GNOME desktop "taking over" the KDE desktop.

---

### Post by freelsjd on 2005-07-22
This problem was finally corrected by logging in under gnome, and setting the preferences everywhere I could find it not to control the desktop background under gnome. Then, when I login under kde, the gnome applications will not try to control the desktop background.

corrected...

---

