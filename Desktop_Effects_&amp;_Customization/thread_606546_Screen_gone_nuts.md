---
title: "Screen gone nuts"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by The_Parasite on 2007-11-08
I'm pretty new to ubuntu, so really need help here.
I was using ubuntu on my notebook, when I decided to connect it to a projecter... nothing happened, so I rebooted.
Then I got a message, that ubuntu couldn't read my drivers for my screen and graphics card, and only showed in 800x600 resullution.

after de-connecting the projector, I still got the same message, so I tried to find my graphics card on the list.
still didn't help, so I tried opening the Drivers-GUI and re-activating the drivers there.
Now my screen resulution is about 320x280, the screen is shown 3 times on top of itself (but a bit off), and I can't see anything on my screen, in order to fix it.

So the help I need, is how to revert my graphic settings, to as they where, before I connected to the projector. (1280x800)
By only using the console, as I am still able to open that.

My graphic card is a ATI MOBILITY RADEON 9600/9700, on a Medion Notebook.

-Steffen

EDIT: Tried re-writing the ect/X11/xorg.conf file from a backup, and now have my screen restored to a 800x600 GUI. Still need help to restoring my original screen resolution though.
- Steffen

EDIT: After getting the GUI back up, it was just a matter of re-writing the xorg.conf file, to match an old backup that worked.
Now everything is up and running again :D
(if anyone is wondering, I used "pico FILENAME" for editing the file in the console, and pressed "Ctrl"+"Alt"+"F1" for getting to the console screen, after booting)
- Steffen

---

### Post by rimoth on 2007-11-08
You can try running.....

sudo dpkg-reconfigure xserver-xorg

---

