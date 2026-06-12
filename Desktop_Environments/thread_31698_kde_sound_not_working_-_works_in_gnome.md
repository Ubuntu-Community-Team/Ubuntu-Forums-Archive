---
title: "kde sound not working - works in gnome"
date: 2005-05-04
forum: Desktop Environments
---

### Post by sage on 2005-05-04
in gnome my sound works fine, but in kde it does not and I get a login error like cannot access /dev/dsp ?  any ideas ?  thks

---

### Post by firas on 2005-05-09
[list]
[*]Did you get any errors during boot? Try "dmesg | less" to view all your boot messages
[*]What's your sound card?
[*]Are the modules for your sound card loaded? Try "lsmod | less" to view all the loaded modules and look for anything starting with a "snd_"
[/list]

---

### Post by Seth on 2005-05-09
libesd-alsa0 ?

---

### Post by sage on 2005-05-09
see the post "Problem with Sound" by aleneski - this is all the same problem.  I boot up with gdk - drumbeat sounds just fine - just when I login a user using kde session do I get the /dev/dsp problem.  I had this same problem a long time ago with another distro - sadly cannot remember what I did to fix it.

---

### Post by firas on 2005-05-10
I've had this problem a long time ago, just can't remember myself either !! Try the following though ...

Check your permissions, I've got :

ls -l /dev/dsp
crw-rw----  1 root audio 14, 3 2005-05-09 21:41 /dev/dsp


Also make sure your user is a member of the audio group:

groups yourusername

---

### Post by sage on 2005-05-11
thks - I added others read to /dev/dsp and enable users to use audio devices - no more error msg - however sound still not working.  Going to Control Center -> Sound System -> Test Sound => sound works.  But then I go to System Notifications -> Play Sound => Nothing !  Also "Apply" button is always deactivated even when I select a new sound.  Any ideas ?

---

### Post by fritsch on 2005-05-19
Hi, just had the same problem, solved it by doing the following:
Controll Center; System sounds; playing settings; choose external player /usr/bin/artsplay

I tried to translate the menu items from german :-)

Fritsch

---

