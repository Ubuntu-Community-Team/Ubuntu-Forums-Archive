---
title: "Ubuntu Won't Load"
date: 2009-01-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wamerida on 2009-01-26
Hi I need some help. I got a dell XPS M1210, with ubuntu 8.04,  last night I Installed thunderbird and remove evolution. this morning Ubuntu will not load. Is loading just the desktop screen, nothing else will load. i can't get access to anything. please help!!!!

---

### Post by nikobor on 2009-01-26
Probably, while removing evolution, you have also removed dependancies like ubuntu-desktop gnome-panel gnome-applets ... This may help you:
apt-get install ubuntu-desktop gnome-panel gnome-applets

---

### Post by ex.pat on 2009-01-26
I did the same on my mini 9. I pushed Ctrl+Alt+Del to be able to log on the terminal. There you can reload the desktop with the above command.

---

### Post by wamerida on 2009-01-26
I rebooted, then went to recovery mode, after that.root Ityped the comands apt-get install ubuntu-desktop gnome-panel gnome-applets.
and the warning is failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.102_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.102_i386.deb)

---

### Post by sarath_it on 2009-01-26
Might have removed even networking.. You will need a Installation CD. Dont need to reinstall, just put it in the cd and try that command.

---

### Post by wamerida on 2009-01-26
how do i do that?  I am freking out. 
Thanks for the help

---

### Post by sarath_it on 2009-01-26
when at blank screen ctrl+alt+f1 to terminal
check /etc/apt/apt.conf.d/00trustcdrom exists 
more /etc/apt/apt.conf.d/00trustcdrom 

Obviously you have another computer with internet. Download the Ubuntu CD from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

make an installation disk..

pop it in to the ubuntu computer, 
sudo apt-get install ubuntu-desktop gnome-panel gnome-applets

---

### Post by wamerida on 2009-01-26
Whell i am happy to tell you thanks for your help. I got it to Work. From the options log into safe terminal sesion use the above comand and done.... Thank you very much

---

### Post by sarath_it on 2009-01-26
Good for you!

---

