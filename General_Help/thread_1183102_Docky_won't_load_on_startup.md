---
title: "Docky won't load on startup"
date: 2009-06-09
forum: General Help
---

### Post by Rocks and Water on 2009-06-09
I just made the transition away from the default bottom panel in Ubuntu to Docky (GNOME Do). It works great, except that it refuses to load on startup, even if I have that option checked. Also, it asks for my default keyring every time it loads. I'm not sure if these two issues are related, but they're certainly frustrating and may force me to use other dockbars such as AWN instead (which is a shame, because I really like Docky's functionality.) Any ideas what the problem could be?

---

### Post by Roinator on 2009-06-21
I believe I have the same problem.

For me, Gnome-do starts at startup, but the docky theme does not work untill I reselect Docky as my theme.  As far as I can tell, it is because the Compiz starts after gnome-do does.  This leads gnome-do to believe there is no composite manager (which is required by docky) so it uses the defult theme as a fall back.  So, sestarting Docky, reloading the window manager (compiz), or reselecting the docky theme in the gnome-do preferences will make docky appear properly.  However, this work around has to be repeated with every log in.

---

### Post by Rocks and Water on 2009-06-21
Well, I fixed the default keyring issue. I had selected the Google Calendars plugin, which was prompting me for the keyring every time I loaded Gnome-Do. Simply removing the plugin addressed the keyring problem. (I don't really need the plugin anyway.)

---

### Post by Roinator on 2009-06-22
Ok, I completely misinterpreted your problem then...
My bad :P

---

### Post by Podex on 2009-07-22
> **Roinator said:**
> I believe I have the same problem.

For me, Gnome-do starts at startup, but the docky theme does not work untill I reselect Docky as my theme.  As far as I can tell, it is because the Compiz starts after gnome-do does.  This leads gnome-do to believe there is no composite manager (which is required by docky) so it uses the defult theme as a fall back.  So, sestarting Docky, reloading the window manager (compiz), or reselecting the docky theme in the gnome-do preferences will make docky appear properly.  However, this work around has to be repeated with every log in.

This problem is mentioned here: [https://bugs.launchpad.net/do/+bug/324332](https://bugs.launchpad.net/do/+bug/324332)
There is a fix for it where you add a delay to the start-up of Gnome-do. It is explained in this thread: [http://ubuntuforums.org/showthread.php?t=1056007](http://ubuntuforums.org/showthread.php?t=1056007)
30 seconds might be overdoing it though, I think 15 is fine (haven't tested it)

---

