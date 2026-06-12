---
title: "Compose key in Ibex"
date: 2009-01-16
forum: General Help
---

### Post by ReelExterminator on 2009-01-16
Hi there,

I'm having a bit of trouble with the Compose Key in my keyboard layout options. Namely under Hardy, I could type any Polish letter using it, but under Ibex, the combination Compose+,;a  doesn't give the letter &#261;, and Compose+,;A doesn't give &#260;. &#552; and &#553; work, though, as does everything else. Does the GTK Compose table change substantially from release to release? I remember a couple of versions back, &#322; and &#321; didn't work. According to the [GtkComposeTable entry]("https://help.ubuntu.com/community/GtkComposeTable") on the Ubuntu wiki, &#261; should be working, but the last-edited date of that page is prior to the release of Ibex.

Thanks!

---

### Post by ReelExterminator on 2009-01-16
I just realized that the &#553; and &#552; I typed above should be &#281; and &#280; based on Wikipedia. If &#281; and &#280; are used more often (I'm not sure if this is the case, but Wikipedia doesn't even have a page on &#552;), should the Compose+,;e and Compose+,;E combinations produce those instead?

---

### Post by ReelExterminator on 2009-01-29
Everyone else's compose key is working well?

---

### Post by ReelExterminator on 2010-09-16
&#260; and &#261; work in 10.04, but &#552; and &#553; are still chosen instead of &#280; and &#281;. I read somewhere that the compose-key sequences are hard-coded into X's source code, and recompiling X seems like it would be a lot more work than copying and pasting...

---

### Post by ReelExterminator on 2010-09-16
Also, the correct characters seem to be listed in the upstream source file which was last updated in 2008: [http://svn.gnome.org/viewvc/gtk%2B/trunk/gtk/gtk-compose-lookaside.txt?view=markup#l279](http://svn.gnome.org/viewvc/gtk%2B/trunk/gtk/gtk-compose-lookaside.txt?view=markup#l279) That's a bit confusing

---

