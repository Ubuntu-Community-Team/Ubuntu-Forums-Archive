---
title: "[SOLVED] What nvidia driver should I be using?"
date: 2008-07-28
forum: Desktop Environments
---

### Post by mattchesters on 2008-07-28
Hello all,
I have an Nvidia FX 5200, and I'm not sure what drivers I should be using. Also I am having struggles with Display Config as it will not let me select the nvidia fx in the drivers list.

As you can guess I'm quite new to Ubuntu (I did have a play with 7.04 last year), so simple explanation will be greatly appreciated. Thank you.

---

### Post by jittopjose on 2008-07-28
my sugestion is first install envyNG using synaptic package manager. in envyNG there is an option to detect hardware and install appropriate driver. its worked fine for me. envyNG will be in system tools menu.

---

### Post by mattchesters on 2008-07-28
No luck there :( sent me back to 640x480. Had to go into recovery mode to get it back to 800x600. If anyone can suggest anything that can get my screen to the correct resolution please help!

---

### Post by benerivo on 2008-07-28
Do you know what nvidia driver you are using and how it was installed (maybe it was installed via the Restricted Drivers Manager). Go in to Synaptic and search for nvidia, so you can see which driver is currently installed.

For a resolution fix, i would have also suggested the envy program, but if this has failed then i would try altering your /etc/X11/xorg.conf file. Can you post the contents of this file here...

   -- The two things above (the driver + xorg.conf), control your graphical display. All the programs such as envy or Display Config, just alter these things to get it right.

I would guess your card would use the nvidia-glx driver, otherwsie it will use the nvidia-glx-new driver.

---

### Post by mattchesters on 2008-07-29
I've finally had success, I edited the xorg.conf, which previous didn't work. The display can run at 60hz, but when I configured it, it showed me no signal. But after editing the resolutions to run at 50, they happily work and run at 60(!?)

Thank you for your help.

---

