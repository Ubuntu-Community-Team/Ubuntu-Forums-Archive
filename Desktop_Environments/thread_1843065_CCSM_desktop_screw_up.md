---
title: "CCSM desktop screw up"
date: 2011-09-12
forum: Desktop Environments
---

### Post by murderd2death on 2011-09-12
i was messing around with some of the settings on ccsm, and out of nowhere the [outline of my desktop disappeared.]("http://imgur.com/25AG3")0i have no way of directly opening any programs, i do not know how to open terminal at this point. at the moment i do have software manager up, i just have no idea what program to install to restore the system to a previous time, or how to get to said program after its installed. please help[-o<

---

### Post by llawwehttam on 2011-09-12
Did a blog post on this a while ago: [http://matt-linux-log.blogspot.com/2010/08/reset-bad-compizconfig-settings-in.html](http://matt-linux-log.blogspot.com/2010/08/reset-bad-compizconfig-settings-in.html)

---

### Post by murderd2death on 2011-09-12
> **llawwehttam said:**
> Did a blog post on this a while ago: [http://matt-linux-log.blogspot.com/2010/08/reset-bad-compizconfig-settings-in.html](http://matt-linux-log.blogspot.com/2010/08/reset-bad-compizconfig-settings-in.html)

this did not work for me
 interestingly enough, i did not need to press ctrl alt f7 to get back to gui, it went back there after the code ```
sudo service gdm start
```but nothing had changed

---

### Post by jeliocranch on 2011-09-12
Yeah, mine too.  I installed compiz config manager after upgrading to 11.04, trying to give unity another shot.  Killed my panels, killed my windows, killed the launcher.  I've read there is no shortcut to get to terminal, and I've read about two that supposedly work, but alas neither do: ctrl+alt+f1, ctrl+alt+T.  
I've got a separate /home partition, so right now even a fresh install doesn't work.  I'm going to try Matt's suggestion via the blog, but I think i'm going to be going in with the liveCD, rm'ing all the hidden docs from all the installs, and doing another fresh install of 10.10.

---

### Post by Krytarik on 2011-09-12
You both, try this troubleshooting guide:
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

It includes this guide, to enable the Cube, if that's what you tried to do:
[http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Greetings.

---

### Post by jeliocranch on 2011-09-13
Great tutorials.  thanks.

After messing about with Matts blog directions and getting no joy, I went in with the liveCD and deleted all the hidden files installed by the multitude of linux distro's I've played with.
I'm pretty sure I killed the install, but haven't tried to boot to it yet.
one thing that's nice about dual booting, you always have some system to boot to.

There is probably a way to reinstall all the files into the home folder from live cd.  Perhaps just examining /home on the CD, and cp .* 
to the other drive.

---

### Post by murderd2death on 2011-09-13
i just backed up my files and reinstalled 11 overnight, and then switched to classic. didnt want to deal with this issue for to long.

---

### Post by jumponskis on 2011-09-13
Hello I ran through your tutorial but to no avail. I successfully created a launcher for ccsm with usr/bin/ccsm yet when I try and open it says Failed to execute child process usr/bin/ccsm (no such directory) :???:

---

### Post by Krytarik on 2011-09-13
jumponskis, did you make sure CCSM is even installed? Also, make sure to set the path right, either "/usr/bin/ccsm" or just "ccsm".

---

### Post by jumponskis on 2011-09-13
solved, went and created gdmsetup launcher, loaded up ubuntu classic, and ran ```
service gdm restart
``` which left me with ubuntu classic. I then went to system>compizconfig settings manager, enabled unity plugin then ran gdmsetup again, re-selected the ubuntu option (unity I suppose) then in terminal ran ```
service gdm restart
``` again and now everything is back to normal.


maybe it was the **/** at the beginning of **/**usr/bin/ccsm that i was forgetting

---

### Post by jeliocranch on 2011-09-14
My last post I had done an```
rm .*
``` in my /home dir after booting to LiveCD and mounting the drive to /media.
Ubuntu wont let you delete . and .., but that's a good thing.

I didn't know if it would boot, but I tried it and it did.  All preferences are forgotten, such as screen savers and all, but just redoing those and all's well.

I'm not super fond of unity.  I've been playing about with Fedora 15, which is running Gnome Shell (gnome 3?) and it seems to provide more options when you need them, and less clutter when you don't.
I think the key to Unity is shortcut keys (basically, not using unity) and the search feature in the launcher.

Anyway, mine is SOLVED.
thanks yall.

---

### Post by sujitrjadhav on 2011-09-14
[SIZE=3]I too faced same problem yesterday due to ccsm. But was able create shortcut to terminal on desktop. Right clicked desktop and created shortcut for konsole. Tried lot of things but none worked. Finally, decided to reinstall ubuntu. Now I am not going to download CCSM again.[/SIZE]

---

