---
title: "System Restore/Recovery Tools??"
date: 2009-02-14
forum: General Help
---

### Post by N9TA on 2009-02-14
Hi gang

Ok....after trying Linux numerous times over the last 15 years I've finally got a rock-em sock-em machine going here. Ubuntu 8.10, 64 bit with all the cool Compiz-Fuzion screen candy/cube thingy...VirtualBox running a virtual Xp installation, MythTV using the TV tuner card!! Let me tell you...I AM THRILLED!! I haven't booted "Vista" in weeks.
Now here's my queery: How can I...or can I...do something like "System Restore" type of deal...where If I manage to screw up my computer (I am VERY good at that) I will be able to "back up" to a known good situation. I know I can back up the whole shebang...but I'm not going to do that....it'd take a whole bunch of DVDs, and the backup may be MONTHS old before I need to use it.
Is there an app that watchs what I do...takes "snap-shots", and allows me to go back if I screw up???

PS: I would NOT have been able to get all this junk working without this forum....not even close!!!  THANKS to all you Linux nerds....Oh GOD....does this mean I'm becomming a Linux Nerd!?!?


                   :-)    Fred

---

### Post by stalkingwolf on 2009-02-14
you can when Grub starts hit ESC. this will bring up the boot menu.

Select the "recovery mode".  It will run its stuff then a window will come up giving you several options.  The second is "repair broken packages".
select this and hit enter. It will tell you when it is finished.  Then you
can fix x server or reboot.

I have read about a system restore like app, but right now I cant recall
what it is called.  The method above has worked well for me, many times.


PS  it takes much less time to do it than it does to tell you about it.

---

### Post by johnjohn2 on 2009-02-14
Stalking wolf hit the nail on the head.

i would also suggest making a separate partition for your home folder as it is easier to restore everything to how it was and you should lose less if you had to restore as all you settings would be saved.

---

### Post by hyper_ch on 2009-02-14
have a look at part image.

And for file backup, I recommend rsync.

---

### Post by lilmagnus on 2009-05-13
Three apps that mimic OSX's Time Machine...

[Back In Time]("http://backintime.le-web.org/")
[Flyback]("http://code.google.com/p/flyback/")
[TimeVault]("https://launchpad.net/timevault/+download")

Seems all rely on rsync anyway but these put a nice GUI on config/maintenance. Back In Time is probably the most attractive. Check out this [review]("http://lifehacker.com/5212899/back-in-time-does-full-linux-backups-in-one-click") from Lifehacker.

Cheers.

---

