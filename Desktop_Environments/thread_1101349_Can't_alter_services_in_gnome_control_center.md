---
title: "Can't alter services in gnome control center"
date: 2009-03-20
forum: Desktop Environments
---

### Post by dcroxton on 2009-03-20
Running XFCE on Hardy with gdm

I'm having one of those problems that make me feel like a total newbie, even though I've been using Linux for years.

I wanted to turn off some services, so I went into the system menu and selected "services."  It came up fine, but the "Unlock" button does nothing, so I can't change anything.  I check some other gnome management tools, and they all had the same problem.  No error, just absolutely no response when clicking on "Unlock."

I thought this might be a problem with gksudo, so I tried running it directly -- only to find out that it's not on my system.  Not only that, but it's not even in my repositories.  I have all the Ubuntu repositories enabled as far as I know (main, universe, multiverse, restricted), and I've never found any broken packages or other problems.

Okay, so maybe it wasn't gksudo.  I decided to log out and back in to the gnome environment, just on a hunch that the gnome tools might need something to be running that I don't have in XFCE.  Even worse:  gnome hangs when I log in, leaving me a blank screen.

I'll worry about the gnome desktop problem later.  Right now, I'm just at a total loss why "Unlock" is not working.  I realize that I could enable or disable services via the command line, but I didn't want to go that route; and now I'm starting to wonder what kind of crazy things are wrong with my system.

---

### Post by chippyafrog on 2009-04-07
Im actually having the same issue, what have you tried to fix it. Im a real newbie here and I wouldn't even know where to start but maybe we can work this one out together

---

### Post by dcroxton on 2009-04-22
I'm not a newbie, but I still had no idea how to go about fixing it. :)  I just lived with it until today, when I stumbled across the following web page:  [http://beginlinux.wordpress.com/2008/07/12/policykit-solutions-with-ubuntu-804/](http://beginlinux.wordpress.com/2008/07/12/policykit-solutions-with-ubuntu-804/).  It explains that you need to re-install policykit.  I didn't see any package errors associated with policykit before today, but, lo and behold, I reinstalled and now I can get into my network manager.  Kind of weird that this didn't get sent out as an update.  It's been almost a year since Hardy was released.

Sincerely,
Derek

---

