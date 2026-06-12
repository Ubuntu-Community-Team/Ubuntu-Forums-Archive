---
title: "Audacity in Wine is messed up"
date: 2006-01-05
forum: Desktop Environments
---

### Post by nalmeth on 2006-01-05
I have a usb mic, which is not picked up by the linux version of audacity. Before, I had used the windows version through wine, which picked it up no problem.

I talked to an administrator on the audacity forum, and regarding the lack of usb mic, he said:

> "Audacity will not find /dev/dsp1 unless there is also a device called /dev/dsp0.  (This is a bug in PortAudio that should be fixed in a future version.)"
"I'll look into this more when I have time.  (I am also using Audacity on Ubuntu, and I have successfully used a USB microphone to record.)"

SO apparently there is a fix to this, but one a developer would be able to do..
I've followed his advice, symlinking various devices, running odd commands, and just can't seem to get it going. 

So after all this, I decided to just go back to Wine Audacity. It has very strange and annoying graphical problems (see attached), but still works. I never had these problems before, and although there has been a new version since, the old one is the same deal. 

DOES ANYONE HAVE ANY IDEA WHY? Is it audacity or wine? Or could it be gnome? Come to think of it I haven't used KDE in some time, possibly since it was last working. I am out of town so I can't try it right now, but its been really bugging me.

> "Audacity has never interacted particularly well with wine, and the last time I tried wine, any windows app took ages to start up and produce a GUI, not just audacity. That may have been a configuration issue in wine though."

---

### Post by stuporglue on 2006-01-05
I'm sorry I don't have an answer to your actual question (wine+audacity), but I think this should fix the /dev/dsp problem. 

Why not just make /dev/dsp0 a symlink to /dev/dsp1? 

See what the permissions are on /dev/dsp1. Note the owner and group especially.

$ sudo ls -l /dev/dsp1
$ sudo ln -s /dev/dsp1 /dev/dsp0
$ sudo chown owner:group /dev/dsp0  (where owner and group are the same as they were on /dev/dsp1)

I think that should make /dev/dsp1 accesable through /dev/dsp0 as well.

---

### Post by nalmeth on 2006-01-05
thank you for reply, I will try when I am home. I am out of town until weekend.

BTW I forgot the attatchment. Here it is.

This is windows version of audacity running under wine under gnome

---

### Post by nalmeth on 2006-01-06
Please could somebody try downloading the Windows version of Audacity and run it in wine to see if they have the same thing come up? 

It's a piss-off.

Thanks any and all

---

### Post by endy on 2006-01-06
Have you tried messaging / loggin a bug with the developers of Audacity?

---

### Post by nalmeth on 2006-01-06
Yes I've been on their forum, and have talked to a developer and an administrator.

They say wine does not interact well with audacity, and that the usb problem is due to a port-audio problem. 

I just want to know if this is only happening to me, because I had it working fine and dandy before.

---

### Post by endy on 2006-01-06
You could try the version of wine from their homepage:

[http://www.winehq.com/site/download-deb]("http://www.winehq.com/site/download-deb")

I can't say if would make any difference but could help :)

---

### Post by nalmeth on 2006-01-06
Good idea

Thanks man

EDIT:
Maybe comiling wine would be a good idea, or installing a different version. I'm willing do try a lot. Ardour could replace audacity for me, but I am very familiar with audacity, and jack is at first sight a pain to install.

Still would like to see someone try wine --> audacity

---

### Post by nalmeth on 2006-01-09
--Bump--

I'm sorry to keep pursuing this, but I would be very appreciative if someone could try the windows version of audacity in wine. It is really bugging me. I need to know if this is an isolated problem.

---

