---
title: "Issues after updates"
date: 2009-05-13
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-05-13
Is any1 else haveing problems after recent updates for jaunty 9.4? I cant really explain in detail, just seems everything is a lil screwy, a lil bit of lagg I guess to say the least. And also cairo-dock will not update...and for some reason it shows about 5 times in system monitor.

---

### Post by kimberlite on 2009-05-13
On cairo-dock update issue see this post: [http://ubuntuforums.org/showthread.php?p=6169870](http://ubuntuforums.org/showthread.php?p=6169870)

Make sure that you use cairo-dock repo ([http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu)). I have uninstalled cairo-dock-data and reinstalled cairo-dock, cairo-dock-plugins. Hope, this will help.

---

### Post by Feelin_froggy8877 on 2009-05-13
In my repo list my distro is still listed as intrepid...what should I enter in the distro line? (Im editing repos in the gui)

(edit) Ima guess jaunty..just wanna be sure

---

### Post by Feelin_froggy8877 on 2009-05-13
Well that worked, but wow...Its eating up mass amounts of cpu and very very laggy with or without opengl, am I the only one with this problem?

---

### Post by kimberlite on 2009-05-14
I do not know your hardware resources, but it is working fine on a toshiba a300 notebook with 2GB RAM. Do you have compiz or other compositor? How much RAM it need to work on your machine?

---

### Post by Feelin_froggy8877 on 2009-05-14
Since I rebooted and started the "no opengl" it seems ok, But I do have an older Geforce mx 440 (64mb) So thats was the issue with opengl, kinda liked them 3d icons too, oh well, Running compiz on a 2.40 ghz p4 w/ 512 mb ram. definitely need to upgrade my ram, but the video card will do for now. thanx for the help.

---

### Post by kimberlite on 2009-05-14
Actually I also encountered some problem with openGL. You may want to consider using "xcompmgr" instead of compiz. It does not have so eye-candy effects, but works fine with metacity and cairo-dock, and consume less memory than compiz. Good luck!

---

