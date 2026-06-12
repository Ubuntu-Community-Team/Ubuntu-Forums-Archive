---
title: "Better Klik Gnome Support"
date: 2006-01-16
forum: Desktop Environments
---

### Post by KillerKiwi on 2006-01-16
Hi every body, klik started out as kde only but here's a bit of code that will hopefully improve the gnome support for klik applications by:
 - Adding a default icon for packages (No more foot icon)
 - Displaying icon for actuall aplication when avalible

To get started first install the klik client press alt F2 and paste
```
wget klik.atekon.de/client/install -O -|sh
```

Next download the attached file extract the script and run it

Restart Firefox

Give a few applications a try
[klik://firefox 1.5]("klik://firefox")
[klik://thunderbird 1.5]("klik://thunderbird")
[klik://skype]("klik://skype")

Hundreds more at [http://klik.atekon.de]("http://klik.atekon.de")

Also an experimintal ifolder (Requires mono to be installed first) at [URL="http://www.yourfilelink.com/get.php?fid=5199"]http://www.yourfilelink.com/get.php?fid=5199
[/URL]

**Please give feedback at [http://klik.atekon.de/wiki/]("http://klik.atekon.de/wiki/") or the [Forum]("http://www.knoppix.net/forum/viewforum.php?f=17")**

These things are currently being worked on for klik
 - [Transparent command line]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#How_can_I_make_.cmg_files_executable_on_the_command_line.3F") 
 - FUSE mounting

---

### Post by newuser111 on 2006-01-16
nice job

but i think the klik icon is a bit too big, it would be better if it were the same size as the rest of the icons on my desktop

running at 1280x1024

---

### Post by KillerKiwi on 2006-01-16
I could default it to 48x48 this seems to be the default size for most icons?

---

### Post by matthewv on 2006-01-16
I agree, the icons are a bit big...

---

### Post by towsonu2003 on 2006-03-03
I had to do this in order to install klik itself. Just in case you need it. [http://klik.atekon.de/wiki/index.php/Troubleshooting#I_get_.22Xdialog:_command_not_found.22](http://klik.atekon.de/wiki/index.php/Troubleshooting#I_get_.22Xdialog:_command_not_found.22)

---

### Post by adamkane on 2006-03-14
[QUOTE=towsonu2003]I had to do this in order to install klik itself. Just in case you need it. [http://klik.atekon.de/wiki/index.php/Troubleshooting#I_get_.22Xdialog:_command_not_found.22](http://klik.atekon.de/wiki/index.php/Troubleshooting#I_get_.22Xdialog:_command_not_found.22)[/QUOTE]

You probably just need to install zenity, dialog, and xdialog to use klik.
```

sudo apt-get install zenity dialog zdialog

```

---

