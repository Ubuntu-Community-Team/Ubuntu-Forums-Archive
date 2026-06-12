---
title: "disable menu scrolling in gnome 2.14"
date: 2007-01-04
forum: Desktop Environments
---

### Post by taelatus on 2007-01-04
I'm currently running Dapper with gnome 2.14.3.  Is there a way to disable menu scrolling?  I want it so that when I click system or applications, I don't have to scroll through a list.

---

### Post by taelatus on 2007-01-05
I have since upgraded to Edgy with gnome 2.16.  I have the same question however.

---

### Post by ross_w on 2007-02-01
Hi, I'm having this problem also, had it on 6.06 and now 6.10, on more than one machine and different architectures (amd64 and x86).. Have looked through gconf-editor but can't find it anywhere. It happens intermittently, and closing the menu and immediately re-opening it expands the menu like it should.

Any ideas? This is very annoying.

---

### Post by lllSpylll on 2007-02-07
This also really annoys me as well.
There must be a setting to disable this.

If anyone knows, I'd love to know.

---

### Post by AndrewMcC on 2007-02-09
Can I bump this thread?

I've had this issue in Dapper, Edgy and now Feisty.  Is it a bug or a feature?  And, as above, can it be disabled?

Thanks,
Andrew

---

### Post by SnowPunk98 on 2007-02-13
I would also like to know, using Edgy and I think Gnome 2.16

---

### Post by SnowPunk98 on 2007-02-18
Anyone know?

---

### Post by neighborlee on 2007-02-18
> **SnowPunk98 said:**
> Anyone know?

I have seen the same problem and its very annoying..it seems none of our englightened devs have a clue on this one...might be time to ask #gnome I guess or their ML.

cheers
nl

---

### Post by SnowPunk98 on 2007-02-20
I guess ill see what Gnome can offer me.

---

### Post by anerewtieooe34223 on 2007-02-25
Possibly caused by menus resizing when icons are loaded.

I use Fedora Core 6 / Clearlooks but adding this worked for me (in 
~/.themes/Clearlooks/gtk2.0/gtkrc):
 
gtk-icon-sizes = "panel-menu=24,24"

You'll need to set the theme name ("Clearlooks" in above example) to whatever you use though.

Note that you may need to create that file.

---

### Post by Mystery00 on 2007-09-29
Same problem here, really annoying, although it seems the default themes for Gnome don't have this bug, only themes I get from gnome-look.org.


Mystery

---

