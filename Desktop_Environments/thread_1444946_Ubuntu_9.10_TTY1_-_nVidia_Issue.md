---
title: "Ubuntu 9.10 TTY1 - nVidia Issue?"
date: 2010-04-02
forum: Desktop Environments
---

### Post by Chris6B on 2010-04-02
I'm VERY new to Ubuntu and Linux in general.

Essentially, I seem to have installed Ubuntu 9.10 successfully(kinda). Upon restarting my machine after the Live CD Install, I'm prompted with a TTY1 install screen.

My Specs:
nVidia 8800GT
Intel e5200 Dual Core CPU
4GB RAM
2 HDDs(Sata) - Dual Booting Win7 and Ubuntu - 1 OS on each HDD


I hear there may be an issue with the nVidia drivers not being installed? I'm VERY new and any detailed instructions would be amazing. I'm looking to break free from Windows.

Also, It may be noted that I am typing this via said install DVD.

I've seen similar posts of this happening but unable to find one that details exactly what I need to do and how to do it in a way I can understand.

Should I download the driver and place it to where it needs to be via the Install Disk? Is there a way to download it via the tty1 menu(easily)?
Is this even the issue? Lol.

Thanks a million,
Chris

---

### Post by Forgotten2191 on 2010-04-02
I'm not entirely sure, but I think it's automatic if you try to enable certain effects.

What I did was made sure I was connected to the internet, then I went to System>Preferences>Appearances, and went to the Visual Effects tab.  I clicked the "Extra" setting, and that got it searching for drivers.

Hope that helped.  Good luck.

---

### Post by Chris6B on 2010-04-02
Thanks Forgotten.

I do this off of the disk, correct?

---

### Post by Forgotten2191 on 2010-04-02
No CD required.  So long as you're connected to the internet, Karmic should be able to locate the drivers.

---

### Post by Chris6B on 2010-04-02
I have NO GUI.

---

### Post by Forgotten2191 on 2010-04-02
Oh, right.  My mistake.

You could try this website:

[http://ubuntuguide.net/install-nvidiaati-graphics-card-driver-in-ubuntu-910karmic](http://ubuntuguide.net/install-nvidiaati-graphics-card-driver-in-ubuntu-910karmic)

In the TTY1 screen, you should be able to run commands, I believe.  Use:

Sudo apt-get install envng-core envyng-qt

Then run it in the TTY1 with:

envyng -t

or

sudo envyng -t

if necessary.

I haven't tried this, but theoretically, it'll bring up a GUI within the TTY1 where you can install drivers.

If that doesn't work, you can try to Google the command for installing nVidia drivers.

---

### Post by Chris6B on 2010-04-03
I fixed it.

I'm at work now. When I come home, I'll post the process.

Essentially I just did a simple update process in TTY1.

It updated my graphics driver and I restarted my computer.

It works and recognizes my 88GT with no problems. 3D Acceleration is enabled and it's running really quickly.

Thanks for your help, Forgotten!

---

