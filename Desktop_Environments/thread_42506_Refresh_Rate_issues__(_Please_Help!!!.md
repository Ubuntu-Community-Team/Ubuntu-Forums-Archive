---
title: "Refresh Rate issues  :( Please Help!!!"
date: 2005-06-17
forum: Desktop Environments
---

### Post by braveerudite on 2005-06-17
](*,)  I'm using the AMD64 Live CD version all works well but one thing... My refresh rate is locked on 61Hz and wont let me change to any other refresh rate. My monitor is brand new and supports higher res. (Gives me 1024X768 with MS Windows XP without a problem so the monitor is not the issue.

I'm looking for a Terminal command (or whatever) that would allow me to change the refresh rate (since I'm using the live version and can't modify files) Please help!!! I would be really greatful. 

PS I'm still a noob to Ubuntu ( and Linux too) and yes I looked all over the Ubuntu wiki and I can't beleive no one has written a Wiki about this. ](*,)

---

### Post by diebels on 2005-06-18
So gnome-display-properties can't change it? Probably the videocard driver is the issue. You can change /etc/X11/xorg.conf while running the live cd.

---

### Post by Phreakazoid on 2005-06-18
I just edit /etc/X11/xorg.conf, find the "Monitor" section and delete or comment out the HorizSync, and VertRefresh lines, then I get the full refresh rate of my monitor when I next restart X.

You can restart X after doing that by pressing ctrl+alt+backspace, make sure you save all data and close all programs though, because they will die when you do that.

---

### Post by braveerudite on 2005-06-18
[QUOTE=diebels]So gnome-display-properties can't change it? Probably the videocard driver is the issue. You can change /etc/X11/xorg.conf while running the live cd.[/QUOTE]
 Thx man... But is there a way to do this with a command? Thx for your help I will try that right now

---

### Post by braveerudite on 2005-06-18
Now is asking me for permission... Now I have to figure out how to get permission to edit a folder of a Live CD... This is crazy.

---

