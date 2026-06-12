---
title: "Install enemy territory"
date: 2007-04-21
forum: Gaming &amp; Leisure
---

### Post by Istonian on 2007-04-21
How do you install Wolfenstein Enemy Territory? Its the latest version 2.60.

---

### Post by Cresho on 2007-04-23
download this from the official website "et-linux-2.55.x86.run"

while thats being downloaded, open terminal and type this. "apt-get install libgtk1.2"  if that doesnt work then do this "sudo apt-get install libgtk1.2" whithout quotes on all.

then cd into  the directory where you have the game like cd /home/yourname/Desktop and then "sudo sh ./et-linux-2.55.x86.run" or "sh ./et-linux-2.55.x86.run" and should start to install.  my problem was that i had perm issues causing my change in settings to be unchanged.  i had to for user install or link path during install i directed into the /home/myname/ and it created a folder which is invisible.  when you open your home directory in the taskbar, go to view, and show hidden folders.  delete .etwolf directory or something like that and the reason being is the perms are screwed.  after deletion restart game and it will recreate directory and no problems.

late.

---

### Post by Cresho on 2007-04-23
here is the updated link

[http://www.ausgamers.com/files/details/html/18074](http://www.ausgamers.com/files/details/html/18074)

ohh and the executable is in the other of the start instead of in the game section

---

