---
title: "Gnome panels and everything royally screwed... help!!"
date: 2005-09-05
forum: Desktop Environments
---

### Post by oofnik on 2005-09-05
So I was messing with icons and themes and applets and things like that. All of a sudden, everything I do crashes wnck-applet. Well that can't be good. But then I discover that when I try to re-add the task list applet to my bottom panel, it crashes again! Ahh! And now, anything I add to the bottom panel crashes wnck-applet. In addition, every time I open nautilus from a launcher, it crashes, and re-opens itself twice. What the hell is going on! This is becoming very frustrating and I have NO IDEA how to go about fixing this. I want to just reset the panel configuration to the default from the way it was installed. Can anyone give me some ideas on how I can do this? ](*,)  ](*,) 

P.S. If I log into GDM as root, everything looks okay. I tried to even add a new user and log in and it's fine too. So it's just a local problem with my username. I don't want to go about setting up the system under a new user because I'd have to reconfigure *all* my settings. So who wants to help? Or maybe I should ask who can help..? I would appreciate it so very much.. thank you everyone.

---

### Post by endy on 2005-09-11
As a last chance thing you can "rm -rf ~/.gnome*" and "rm -rf ~/.gconf*". That should pretty much delete all of gnome's settings. Log out and back in and you should have a default desktop again. Backup the directories before hand if you like, and if it goes wrong some how you can always just copy them back :)

---

### Post by rafakl on 2005-09-11
Or you can try reinstalling the the desktop with:

sudo apt-get --reinstall ubuntu-desktop

 :razz:

---

### Post by webhead on 2005-10-11
Well, I tried both of these suggestions, and niether worked.  Any more ideas?

Dan

---
Breezy was wroking so well.

---

### Post by Snocrash on 2005-10-11
Well.....if you screwed your Gnome settings database, I'm not sure if you can just reset it without loosing all your settings. But, for the fun of it...is there an error message if you try to start nautilus from a terminal????

Also try adding rm -Rf .nautil* along with the other 2.

Course...you could always rename the user home folder, log back in and let it create a new one and then start copying the old stuff over one at a time until you find the problem.

Best of luck,

 -Sno

---

