---
title: "Some apps won't start"
date: 2008-08-22
forum: Desktop Environments
---

### Post by antknee869 on 2008-08-22
I have two apps: VMware and Pidgin that won't start when I click on the start menu icon. First it was VMware, so I thought it was a problem with just that app. But now Pidgin won't start either. Both apps don't give any errors, they just say "starting up" in the taskbar then go away after a few seconds.
What could be causing this?
Thanks

---

### Post by Iandefor on 2008-08-22
Try running them both from the terminal. I don't know what you'd do for VMWare, but for pidgin, just do ```
pidgin
``` from a terminal.

---

### Post by freddyg on 2008-08-22
I have the same problem with pidgin, starting in terminal gives no messages. just goes back to the prompt.

---

### Post by my_key on 2008-08-22
I had this problem once when my drive (in my case my home partition) was entirely full. That way app's couldn't make temp files and the like...

---

### Post by freddyg on 2008-08-22
ok, not much of a solution, but i uninstalled pidgin and grbbed the debs for 2.5.0 from getdeb. but i had a thought afterwords, check system monitor to see if its running but not displaying or something. i dont know how to fix that either, but might be a start.

oh yeah, make sure to grab all 3 components and start the install with pidgin-data and then libpurple and finally pidgin

---

### Post by dcsutton on 2008-08-26
I'm having this very same problem - it's most any program after my machine has been on for some time. At the moment, it's tomboy notes, but more often than not it'll be firefox.

I've found that they are, in fact, still running - but not displaying. Anyone have any ideas?

---

