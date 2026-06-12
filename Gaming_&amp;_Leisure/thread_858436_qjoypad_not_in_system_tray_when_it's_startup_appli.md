---
title: "qjoypad not in system tray when it's startup application"
date: 2008-07-13
forum: Gaming &amp; Leisure
---

### Post by juanitobanana on 2008-07-13
Hello,

I know this qjoypad program must be difficult because apparently is not maintained anymore, but It is extremely useful to some games that just can't recognize the joystick. I personally usi it most of all as a remote controller.

Anyway, the problem is that I put it on start-up applications and it opens on a very tiny window in the middle of the sreen. I assume this is a gnome problem since when I close it and open it again it goes to the system tray as it should. Anyone could give me a hint on how to solve this specific problem?

Thanks

---

### Post by plmegalo on 2008-07-14
> **juanitobanana said:**
> Hello,

I know this qjoypad program must be difficult because apparently is not maintained anymore, but It is extremely useful to some games that just can't recognize the joystick. I personally usi it most of all as a remote controller.

Anyway, the problem is that I put it on start-up applications and it opens on a very tiny window in the middle of the sreen. I assume this is a gnome problem since when I close it and open it again it goes to the system tray as it should. Anyone could give me a hint on how to solve this specific problem?

Thanks

I use it too and find it really useful.

What version have you installed ?
If it can help some version have been provided by users.
You'll find information in this thread :
[http://ubuntuforums.org/archive/index.php/t-147918.html](http://ubuntuforums.org/archive/index.php/t-147918.html)

A version modified to work with latest kernel here :
[http://www.azriek.fr/index.php?post/2007/10/07/qjoypad-ubuntu-gutsy-et-occupation-CPU-a-100](http://www.azriek.fr/index.php?post/2007/10/07/qjoypad-ubuntu-gutsy-et-occupation-CPU-a-100)

And can directly download a .deb to apply on ubuntu here :
[http://www.azriek.fr/divers/qjoypad_3.4.2-1_i386.deb](http://www.azriek.fr/divers/qjoypad_3.4.2-1_i386.deb)

Hope this can help
Have fun

---

### Post by juanitobanana on 2008-07-16
Hello, and thanks for the answer..

I am in fact using it without a problem, the only detail is that when I include it on the "start-up applications", It fails to put the qjoypad icon on the system tray. If I close it and open it again, it goes to the system tray without any problem. I am not reporting that it doesn't work or anything, it works perfectly.. but I think this behaviour might be a bug from the "start-up applications" manager instead.. Do I report this as a bug?

---

### Post by plmegalo on 2008-07-17
> **juanitobanana said:**
> Hello, and thanks for the answer..

I am in fact using it without a problem, the only detail is that when I include it on the "start-up applications", It fails to put the qjoypad icon on the system tray. If I close it and open it again, it goes to the system tray without any problem. I am not reporting that it doesn't work or anything, it works perfectly.. but I think this behaviour might be a bug from the "start-up applications" manager instead.. Do I report this as a bug?

Ok, sorry, I didn't understood. I was having the same problem under KDE (with other startup problems that you shouldn't have with gnome) and I made a script that waits about 5 seconds to launch it.
The command to use is "sleep 5" in the shell script.
It works fine for me.
But I also gave you the last version information, because it seems older versions have had this "system tray" issue before.
If you need, I will post the all script later (I'm not currently on my home computer).

---

### Post by juanitobanana on 2008-07-18
Thanks, I was thinking about doing that.. I prefer doing the script myself so I can finally learn..

I reported a bug in gnome bugtracker..

quick question though.. your script is in sh or bash? does it matter?

thanks

---

### Post by plmegalo on 2008-07-20
> **juanitobanana said:**
> ...

quick question though.. your script is in sh or bash? does it matter?

thanks

simple sh
but I think this doesn't really matter, it should work anyway with both sh and bash.

---

### Post by juanitobanana on 2008-07-26
Hello,

I took my time, but this didn't solve the problem unfortunately.. the script makes it wait for 5 seconds but still opens in a non system tray window..

someone has any other idea?

many thanks

---

