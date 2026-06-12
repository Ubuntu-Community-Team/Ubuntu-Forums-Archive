---
title: "Gnome Hang &quot;Acpid: client 1146 [0:0] has disconnected"
date: 2015-01-10
forum: Desktop Environments
---

### Post by arlenn2 on 2015-01-10
I am getting a weird cyclical hang of unity/gnome in a clean 14.04 install.  evey ~hour? the GUI will hang.  Bailing out to console (ctrl+alt+f2) and back into graphics (ctrl+alt+f7) restores a functioning desktop with some screen corruption that can be cleaned up with a application minimise+maximise. 

I am mostly seeing this with Firefox, but that is mostly what I have been using lately... I cant confirm that it is entirely related to firefox.

this is all on a Dell inspiron 15 7000 with nvidia 750 graphics with binary "updates" driver.

Its not a show stopper, but really bloody annoying.

Thanks for your help

Appears not related to firefox.  
The session stays active even though not responsive as returning to the graphics session, the graphics session has updated to activity performed while hung (changing windows using touch screen) etc.
1146 is Xorg.

---

### Post by arlenn2 on 2015-01-11
Edit: scratch that, just froze, again.




It has been working well today... let see if it remains.

I changed the power option in the nvdia control panel from "auto" to "adaptive"
I commented out the bus vectors of the intel and nvidia GPUs from Xorg.conf, which the driver promptly put back.

But seems to be better today.

---

### Post by arlenn2 on 2015-01-12
Seems to be stable with using the embedded intel GPU.  no issues.  The Intel driver was selected using the Nvidia control panel.

---

