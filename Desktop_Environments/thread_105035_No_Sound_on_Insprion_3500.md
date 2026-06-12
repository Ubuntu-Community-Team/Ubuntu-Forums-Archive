---
title: "No Sound on Insprion 3500"
date: 2005-12-17
forum: Desktop Environments
---

### Post by xftnfnb7 on 2005-12-17
After installing Ubuntu on an Inspiron 3500 I notice that I have not sound at all.  I do get two beeps when the system boots up but after that nothing.  There is an "X" next to the volume control in the panel a the top left of the screen.  Any thoughts....

---

### Post by bikeracer on 2006-01-05
I have the same problem.  I can't figure out how to get it working, and I've searched for the answer.  I would love to find a step-by-step guide since I am new to Linux.

---

### Post by Sef on 2006-01-05
This is from the Unofficial Ubuntu 5.04 Starter Guide

[http://www.ubuntuguide.org]("http://www.ubuntuguide.org/#synchronizingclocktooslow")   It's under Troubleshooting toward the end.

(Yes, this is from 5.04 Hoary, but it should work.  If someone more technically proficient than me knows of any changes post them here.)


Q: How to configure sound to work properly in GNOME?

   1. Read General Notes
   2. Read How to add extra repositories?
   3.

sudo killall esd
sudo cp /etc/esound/esd.conf /etc/esound/esd.conf_backup
sudo gedit /etc/esound/esd.conf

   4. Find this section

...
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
...

   5. Replace with the following lines

auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default

   6. Save the edited file (sample)
   7.

sudo apt-get install libesd-alsa0
sudo gedit /etc/asound.conf

   8. Insert the following lines into the new file

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

   9. Save the edited file (sample)
  10.

sudo ln -fs /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

  11. System -> Preferences -> Sound
  12. Sound preferences

General Tab -> Sounds for events (Un-Checked)

  13. Save and close all opened applications, Reboot computer

---

### Post by bikeracer on 2006-01-09
Thanks Sef.  But, this didn't work.  I suspect it only fixes sound issues with gnome, and not the hardware driver issues we Inspiron 3500 users have.

I'm pretty sure no sound driver ever gets loaded, but I don't see any errors during boot.

---

### Post by gosh on 2006-01-09
I had the same problem on my Inspiron 7000.

The following worked.
You are probably not in the audio group

At the terminal type id.
Mine shows:
uid=1000(jos) gid=1000(jos) groups=4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),104(lpadmin),105(scanner),106(admin),1000(jos)

As you can see I am a member of the audio groep.
To add do:
sudo gedit /etc/group
Put your name next to audio
audio: x:29:jos

Then restart your computer

---

### Post by bikeracer on 2006-01-09
Thanks gosh, but that isn't it either, I'm listed in the audio group.

I don't know how to set up the nm256 sound driver.  Can anyone walk me through picking/configuring a driver?

This bug:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=9107](https://bugzilla.ubuntu.com/show_bug.cgi?id=9107)

seems to indicate setting a force_ac97 option might work.

But, I don't know how to enable the driver, let alone how/where to add that ac97 option.

---

