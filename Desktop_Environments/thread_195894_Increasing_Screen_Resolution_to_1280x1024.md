---
title: "Increasing Screen Resolution to 1280x1024"
date: 2006-06-13
forum: Desktop Environments
---

### Post by Stan Stansbury on 2006-06-13
Hi,
I'm new to Linux and Ubuntu and may be doing something dumb. I've just installed it, and thing are working well mostly.

The issue is that my monitor supports 1280x1024, but Ubuntu's screen resolution options only go as high as 1024x768. I do not know where to go or what to do to increase the resolution.

Can anyone out there point me in the right direction?

Thanks in advance.

---

### Post by CronoDekar on 2006-06-13
What you need to do is modify your xorg.conf.  Fortunately there's a little program to do that automatically for you.  First though, you'll want to backup that file just in case anything goes wrong.  In terminal, enter:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```

Then do this (though be sure you've got everything else you're doing saved and taken care of, you'll be leaving GUI-land):

```

sudo dpkg-reconfigure xserver-xorg

```

Suddenly you'll appear in a text thing which sets up xorg.conf.  Now most of these options you'll probably want to keep as-is, so just hit Enter for most of the stuff.  Eventually though you'll get a list of screen resolutions -- hit the space bar to activate 1280x1024 and add it to the list.  Keep pressing enter through the defaults, and when you're out, hit Ctrl-Alt-Backspace or do sudo reboot.

Hopefully everything should be fine and dandy (I had to do this too), but if not just do:

```

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

```

to restore your backup file.

---

### Post by ubnoobie on 2006-06-13
see [https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

---

