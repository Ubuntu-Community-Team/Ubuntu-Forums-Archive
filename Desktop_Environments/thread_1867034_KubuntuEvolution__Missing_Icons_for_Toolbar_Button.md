---
title: "Kubuntu/Evolution:  Missing Icons for Toolbar Buttons"
date: 2011-10-22
forum: Desktop Environments
---

### Post by drumz on 2011-10-22
I'm running the latest Kubuntu (11.10) upgraded from the previous release.  I use evolution as my email client and now after the upgrade many of the buttons in the toolbar no longer display an icon.

Launching evolution from the command line results in the following indicating this is a theme related issue:

```
(evolution:9780): e-table-WARNING **: Icon 'mail-unread' not present in theme
(evolution:9780): e-table-WARNING **: Icon 'mail-read' not present in theme
(evolution:9780): e-table-WARNING **: Icon 'mail-replied' not present in theme
(evolution:9780): e-table-WARNING **: Icon 'mail-forward' not present in theme
(evolution:9780): e-table-WARNING **: Icon 'emblem-important' not present in theme
(evolution:9780): e-table-WARNING **: Icon 'mail-unread' not present in theme
(evolution:9780): e-table-WARNING **: Icon 'emblem-important' not present in theme

```

What additional packages do I need to install to get the icons?  I've tried installing a few additional theme related packages but so far no luck.

Thanks!

---

### Post by scharacter on 2011-11-07
I have the same issue, did you ever get resolution on this?

thanks in advance.

---

### Post by drumz on 2011-11-07
Nope.  Unfortunately I haven't been able to track down a solution for this one yet.

---

### Post by Mr_Bumpy on 2011-12-23
I just upgraded my mom's PC to Kubuntu 11.10, and noticed the same thing: missing icons and ugly theme in Evolution.  The ugly theme is because oxygen-gtk doesn't theme gtk3 apps yet (although this is in the works).  I solved this by installing the Zukitwo gtk3 theme, but other gtk3 themes should work as well.

Here are instructions that will resolve both the missing icons and the ugly theme issues:
[LIST=1]
[*]Install the following packages: **gtk3-engines-unico gtk2-engines-murrine gtk2-engines-pixbuf humanity-icon-theme**
[*]Download the [Zukitwo theme]("http://gnome-look.org/content/show.php/Zukitwo?content=140562") from gnome-look.org.
[*]Follow the included instructions to install it (installing to ~/.themes works fine).
[*]Create the file **/home/username/.config/gtk-3.0/settings.ini** (replacing "username" with your login name) with the following contents:
```
[Settings]
gtk-theme-name = Zukitwo
gtk-fallback-icon-theme = Humanity
# next option is applicable only if selected theme supports it
gtk-application-prefer-dark-theme = false
# set font name and dimension
gtk-font-name = Ubuntu 9
```
[/LIST]
There you go.  GTK3 apps should now look a lot nicer.

---

### Post by drumz on 2011-12-23
Mr_Bumpy:  

Thank you thank you thank you!!!

Followed your directions (with the exclusion of installing the theme to /usr/share/theme) and it worked perfectly!!  Once installed all I had to do was exit evolution and then relaunch it and it came back up looking much cleaner and with the icons.

(Be glad you weren't here to see my happy dance, it's pretty ugly!)

Thanks!

---

### Post by inobe on 2011-12-23
drumz, why did you go with evolution instead of kmail.

curious is all, thanks

---

### Post by drumz on 2011-12-23
No particular reason other than I've used it for years - at the point I started using it I don't think KMail existed or it wasn't as feature rich at the time.  I've amassed years worth of email and just haven't felt motivated to switch/import to another email client.

---

### Post by drumz on 2012-10-21
Just following up with this in regard to the latest release (12.10).  Every other line in the message from/subject/date area was unreadable (white text on white background).  Remembering the changes made here I simply deleted  /home/<usernam>/.config/gtk-3.0 , exited evolution and restarted it and it was fine.

---

