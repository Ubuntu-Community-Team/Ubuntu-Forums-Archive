---
title: "No sound after suspend ???"
date: 2009-02-28
forum: General Help
---

### Post by sapple on 2009-02-28
Hello, I am new to Ubuntu and I have a problem.

My sound works fine, but **if I suspend my laptop and then come back after sometime, I get no sound.**.. I checked my volume controls and they are all turned on.

If I restart the computer, I get my sound back.

So, how do I fix this problem?

---

### Post by sapple on 2009-02-28
note: i am using ubuntu 8.04(hardy) 64-bit version

---

### Post by empty_spaces on 2009-02-28
I believe this problem occurs in 8.04 because the sound modules are not properly unloaded and loaded at suspend and resume.
I played a lot with my settings to solve this, but in the end I had to settle for a dirty fix - running **sudo /sbin/alsa force-reload** in the terminal.
Running this will cause the volume applet in the desktop panel to restart, just click ok when that message pops up.
After this your sound should work.

Again, this is a dirty fix and someone might have a better solution for this.

---

### Post by sapple on 2009-03-01
yes, it works but isn't there another way of fixing this problem. Do I have to type that command after every suspension?

---

### Post by empty_spaces on 2009-03-01
yup, which is why I said it was a dirty fix.
I actually had a launcher in my taskbar to run that command everytime I resumed from suspend. I don't have that issue with 8.10 anymore.

---

### Post by sapple on 2009-03-02
how do you create a launcher? I tried keybinding but it didn't work??

---

### Post by empty_spaces on 2009-03-02
Just right-click on the panel, and select **Custom Application Launcher**.
The type can be **Application** or **Application in Terminal** (The last time I did this, **Application** would not work so I used **Application in Terminal**).
Give it any name you want and type in the command to reload alsa.
Click OK, and you should be good to go.

---

### Post by sapple on 2009-03-02
thank you, it works now. However, the Ubuntu people should correct this mistake..

---

