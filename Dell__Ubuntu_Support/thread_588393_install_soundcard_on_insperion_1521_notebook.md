---
title: "install soundcard on insperion 1521 notebook"
date: 2007-10-23
forum: Dell  Ubuntu Support
---

### Post by mrpddnos on 2007-10-23
hiya all,

Im a complete newby to linux. I made a dualboot on mt insperion 1521 notebook today (vista/ubuntu). Durin the install there were no problems. 

After the installation i noticed that my soundcard has not been installed. how can I install it?

yours,
bernhard

---

### Post by will_ship on 2007-10-25
I was in the same boat as you. see my thread at 

[http://ubuntuforums.org/showthread.php?t=580732&highlight=1521](http://ubuntuforums.org/showthread.php?t=580732&highlight=1521)

Hope It works for you...

---

### Post by will_ship on 2007-10-25
If you have any other problems with the 1521 check out my other threads.

---

### Post by GIFRATE on 2007-10-25
I also had this problem, and trying different solution found on this forum didn't solve anything : installing new alsa, adding also module or installing backport kernel module; found in this thread:

[http://ubuntuforums.org/showthread.php?t=577469]("http://ubuntuforums.org/showthread.php?t=577469")

Reading further down, you'll find that the wrong alsa driver for the 1521 are installed, and typing this into the terminal:

[COLOR="Blue"]sudo apt-get remove alsa[/COLOR]

and then [COLOR="blue"]rebooting [/COLOR]would fix the sound problem.

Good luck

---

### Post by b52087 on 2007-11-26
Hello
I am seriously considering upgrading to Linux from Windows Vista.
I've recently purchased 3 Dell Inspiron 1521 for myself & my kids, and what a major disappointment Vista is!!! I don't see what the big deal is with Microsoft. I've tried Linux Redhat years ago, but would like to become more familiar with this more stable OS, as well as my kids, since I can now see what Linux is capable of...._**[http://ca.youtube.com/watch?v=4JYokZ4rv-0&feature=related](http://ca.youtube.com/watch?v=4JYokZ4rv-0&feature=related)**_
All I can say is...Awesome!!!!
I want my laptop to do that.
Anyways, i've downloaded Ubuntu 7.10 alternate iso for i386 & live CD amd64 iso files.
Hope wireless, video & sound works. 
Bye for now

---

