---
title: "libsane-extras-rules"
date: 2009-01-16
forum: General Help
---

### Post by Indyviews on 2009-01-16
Does anyone know how to bring up libsane-extras-rules?

I have tried:

sudo gedit /etc/udev/rules.d/50-libsane-extras-rules

An empty box shows up and never does anything...I have waited as much as five hours or more. I am thinking that I am at the point that if I can get the list and make a change, that I will be able to use my scanner. I would appreciate any help.

---

### Post by mc4man on 2009-01-16
rules files always end in .rules

When you gedit a file and it comes up blank there's 3 possibilities
the file exists but you used the wrong path
you used the right path but the file is empty
the file doesn't exist

When you close gedit out if you choosed save then in 2 of the above you'll have created a new file at that location with that name.

I'd suggest browsing to confirm the file exists and to get correct path.

You may want to post what version of ubuntu your using.

---

### Post by Indyviews on 2009-01-16
Thanks **mc4man**, I got the list of scanners and made the change that this certain thread mentioned....(664 to 666) and now my scanner appears to be found on the terminal.

Two questions if anyone can help (without another thread):

I ran sane as a last step and I got: (xsane:5875): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

**My big question** is running sane doesn't make sense to me. I just want my scanner controls back so I can scan some images. I am lost at this stage.

I am running Ubuntu 8.10 and I have an Epson Perfection 3170 scanner. Any help anyone?

---

### Post by mc4man on 2009-01-16
I've never run a scanner in ubuntu, though I see there's a epson perfection 1650 up on the shelf.
If you don't get it resolved maybe later I'll try hooking it up and see what gives.

Do you have a link to the thread you mentioned?

---

### Post by Indyviews on 2009-01-16
The link is: [http://ubuntuforums.org/showthread.php?t=1028064](http://ubuntuforums.org/showthread.php?t=1028064) This is just one of the threads I am trying to make sense of. I am down to where it says to reboot. I have just posted another thread about five minutes ago..perhaps you could help on it. I am about to give up..I have a great scanner and with limited income, I can't see going out and buying another $200 plus scanner.

---

