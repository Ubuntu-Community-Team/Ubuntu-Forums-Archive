---
title: "Not able to login to Ubuntu 10.04. - Power manger not Installed Properly."
date: 2010-11-28
forum: Desktop Environments
---

### Post by tattushenoi on 2010-11-28
ello All,

I have 10.04 installed on one partition and Xp on another. One of the partitions is just data.

I had bittorrentclient installed in my linux. It got stuck somewhere and I restarted. After that my Ubuntu doesnt log in. It asks me to enter user  name and password with a blue login window instead or usual color[orange?]. It has 3 options as well - Gnome failsafe, Gnome, xterm.

But no matter how many times I enter username and password, it doesnt login and comes back to login window. It also shows on the top right corner that Gnome power manger has not been configured properly and says 'install problems'.

I have tried going into recovery mode and tried " fix broken packages". But still the issue persists. 

I have tried going to root from recovery and typing 'dpkg-reconfigure gconf. But it says gconf not installed. 

then I tried sudo apt-get install gnome. But it says some broken packages...could not install and all that. it says something about epiphany too.

Then tried sudo apt-get --reinstall install ubuntu-desktop as well.

Gave sudo apt-get update and sudo apt-get upgrade.

But nothing seems to work. Its still blue login window with a black screen behind and not allowing me to login.

My grub has been updated to 'something'.26. The versions 25,24,23 and 22 are also there. I tried entering through all of those too.

please help.

---

### Post by garvinrick4 on 2010-11-28
What were you doing when machine got "stuck". Upgrading, dist-upgrade?

---

### Post by tattushenoi on 2010-11-28
nothing...I just started my system...started bit torrent client....and yeah the update manager window had come up....but I had not clicked 'Install Updates' yet...so it would not have downloaded or started install...but the whole thing got stuck and I could close the update manager window[without doing anything with it]and  had to restart....

---

### Post by tattushenoi on 2010-11-28
please help...I am not able to login ...

---

### Post by tattushenoi on 2010-11-28
Some one who could help me?

---

### Post by tattushenoi on 2010-12-03
Any one?

Please....Its urgent..I need my system working by today evening....

any other option other than Format all over again?

---

### Post by tattushenoi on 2010-12-04
Well, the system is still ****** up! I am really thinking of ditching this thing. 

But if any solution is available other than format it would be a welcome relief.

I have tried sudo apt-get update "upgrade dpkg --configure -a
install ubuntu-desktop

install gnome-power-manager 

etc etc..nothing works.....

Please guys...some help? Or is there no solution?

---

### Post by tattushenoi on 2010-12-04
Well, there has been some progress! I cleaned up some space using rm and rmdir...

Now I got the old and usual color of the login window back and I dont get the login window back. But now the problem is, after loggin in, I get a blank screen with nothing on it. No menu, No icons, nothing. Just the screen with usual color.

What should I do now?

---

### Post by tattushenoi on 2010-12-04
Is there any one who is active in this forum except me ?:p

---

### Post by tattushenoi on 2010-12-05
any solution to see the menu and disks after login??any one?

---

