---
title: "XGL session won't start"
date: 2007-07-30
forum: Desktop Effects &amp; Customization
---

### Post by ubunteen on 2007-07-30
Well, after hours upon hours of tweaking and installing, I finally got XGL and compiz fusion to work with my ATI card.  Well, it's worked for a week or so now.  Today, though, when I logged in to the XGL session in KDM, it brought me straight back to the KDM login.  Usually, it just does a couple of strange flashes, shows the "loading" thing, and goes to the desktop.

I know a couple of people have had this problem in Gnome, but I've not heard of it being solved in a Kubuntu setting.

---

### Post by tupesadilla on 2007-07-30
i've had that problem with gnome, i suppose KDE would be the same, can you start a failsafe session? or try ```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure the xserver to hopefully get your desktop back, then go from there

---

### Post by ubunteen on 2007-07-30
So, I did that and poorly configured it.  This resulted in kdm never even starting on next boot.  I then used the backup xorg.conf file instead of my new one.  I still have the same problem.  Now I'm not only w/o Xgl, but also w/o kdm or anything resembling a GUI whatsoever.  I think kdm ix just hanging, because I get the watch icon on a black bg and i can move it, but it stays there.  And when I ctrl-alt-f8, it says the last thing it got an ok on is something about rc.local.  I'm not sure if that's always there though.

---

### Post by ubunteen on 2007-07-31
well, I guess you can call this a bump, because I'm back to my original problem.  However, I've noticed in my xorg.conf file the the "composite" option has a value of 0.  I know that should be 1, but I got to thinking.  I had to mess w/ that file when I installed Xgl and I can't remember what I had to do.  I'll be searching around ubuntuforums, but help would be appreciated.

---

### Post by hardKNOXbz on 2007-08-03
i also have the same problem but it doesnt bother me so much since i don't log on to XGL session much

---

