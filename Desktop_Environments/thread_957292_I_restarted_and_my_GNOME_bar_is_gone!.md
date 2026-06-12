---
title: "I restarted and my GNOME bar is gone!"
date: 2008-10-24
forum: Desktop Environments
---

### Post by zachbb on 2008-10-24
hello

I am new to ubuntu (and linux).

I turned on my computer this morning and the top bar (in GNOME) with applications, places and system (i think), and with the battery life and wifi on the right is gone.

The trash icon is also gone from the bottom right, and the desktop icon is also gone from the bottom left.

They are just grey bars with no icons in them.

Yesterday I created a terminal shortcut on my desktop, but when I double click it, the terminal window opens but there is no prompt..

I'm back on windows whilst I wait.. Any ideas about how to fix this?

Thanks

Zach

---

### Post by buster2209 on 2008-10-31
This happened to me.  I think it's a bug

I solved it like this;

ctrl + alt + F2.  
This brings up the terminal.  
Enter ur username and password.  
Enter 'Gnome-panel' (minus quotation marks).  
It will probaly tell you it isn't installed.  
Enter 'sudo apt-get install gnome-panel' (minus quotation marks).  
This will install the missing toolbar.  
ctrl + alt + F7 will take you back to the desktop. 
 
ctrl + alt + del and choose restart.  IF this doesn't work, just unpluf ur PC

When your computer boots up, the bars should be back but some apps within the panel wont work - namely trash.

Go to 'Synaptics Package Manager' and install 'Gnome-desktop-data'

Restart

All should be good now.

This only happened to me once.  Usually the first time you make theme changes and restart

Hope this helps

---

### Post by zachbb on 2008-11-01
Thanks a lot for your help, it works now.

Yes, I think it's a big too.. I posted a bug report in case it is.

Thanks again!

---

