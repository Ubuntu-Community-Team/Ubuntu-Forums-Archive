---
title: "Couple of problems - screen res and desktop effects"
date: 2008-04-30
forum: Desktop Environments
---

### Post by hatman on 2008-04-30
Took the opportunity of Hardy's release  to remove the Win9x partition/dual boot from my system.  Loaded Hardy, added everything I needed to add... great stuff... Got it all up and running, changed the screen res to 1280x1024 and saved it added Compiz Settings Manager... everything running ok... 

Re-booted.. came up in 800x600... Odd... Went to up screen resolution, put it back to 1280 using nVidia X Server settings... Lost title bars when it went back to higher res... 

Searched on forums, found solution (metacity  --replace), this appeared to work... Re-booted again, back to 800x600, took it back to 1280 using nVidia X Server settings clicked on Save to X Configuration File to save settings and got error that it cant write to /etc/X11/xorg.conf. Looked at what it was going to write, pulled up a terminal, copied and pasted info into xorg.conf (yes, I backed it up first)... Re-booted.. again 800x600... but this time when I changed it back to 1280 when I clicked on Save to X Config File I got this message "Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'."  

And every time I put it back to 1280 I lose the title bar and have to open a terminal window and type "metacity --replace" to get them back.. now none of the advanced desktop settings are working, even though they are all set (include Windows Decoration, which one help topic reply suggested) and I've even re-installed them through Synaptic, but to no avail...

Any ideas? I'm just going round in circles.. Need to get the diplay to start up in 1280x1024 everytimer and get the Advanced Desktop Settings working again.. preferably leaving my title bars in place...!!!

TIA

---

### Post by Gannin on 2008-04-30
You need to run nvidia-settings from the command line with sudo, like "sudo nvidia-settings".  That way, when you click the button to save the configuration, it'll actually save.  Otherwise, it's trying to save the configuration to xorg.conf with your current user permissions, which aren't enough to write to the file.

---

### Post by hatman on 2008-04-30
DOH! I never thought of that, and that should have been one of the first things I did... But I think you go round and round and forget the simple easy things sometimes...

Now to try and get those Compiz Effects going... Blindin thing works great on my work PC...

---

