---
title: "ubuntu kubuntu mess up."
date: 2012-01-16
forum: Desktop Environments
---

### Post by Asad3ainJalout on 2012-01-16
So I have ubuntu, i installed the Kubuntu desktop using the command
> Sudo apt-get install kubuntu-desktop
After using it for a while i wanted to get rid of it, bear in mind I use a laptop and it was using too many system rescources. 
I used the command
> Sudo apt-get remove kubuntu-desktop

Well it would not remove, because it is running one process. It runs my bootmenu (when i pick my OS in the dual boot(i explain because I am not certain of the correct terms (noob here))) and my login. I have all parts of it uninstalled except for that one small part. I would like to make that menu and the login screen back to ubuntu if possible.

Thank you :D

I do not want to start experiencing with gnome 3 shell till i fix this issue.

---

### Post by am_i_registered on 2012-01-17
here is the best solution in my opinion:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by ktucker5301 on 2012-01-17
I had a similar issue with unity lightdm crashing, making it impossible to log into my system. with a GRUB boot disk I was able to log in under single user and change the desktop environment to Gnome (GDM). you may need to boot into single user to change your desktop environment from KDE back to Gnome

---

