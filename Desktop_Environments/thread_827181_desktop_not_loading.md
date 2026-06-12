---
title: "desktop not loading"
date: 2008-06-12
forum: Desktop Environments
---

### Post by 133794m3r on 2008-06-12
Ok, my desktop isn't loading. Normally if I was still using Windows XP I would say that the Explorer.exe wasn't working and I'd open up Task Manager, and then start it myself. But since this is Ubuntu derivative of Linux, I have no idea whatsoever about what to do now. I know that there is probably something simple to do but I have no idea. I don't see anything. I see my mouse and my background. I right click and nothing happens. I press ctrl+alt+delete and that seems to work but nothing else. I haven't tried the alt+F2 thing... and tried terminal b/c I don't know my way around it that well. I'm hoping that it's something minor... but if it isn't then I guess I'll have to wipe my HDD again.

---

### Post by kdcoetzee on 2008-06-12
You can restart gnome desktop with crtl-alt-backspace.

If you changed something in your xorg.conf file you can try to reconfigure it. But then you need to go to the terminal with alt-F1 

Login and type
     dpkg-reconfigure xserver-xorg

You will need to know your hardware. it will ask you a few question.

---

### Post by 133794m3r on 2008-06-12
I'll try that thanks for the help thus far...

---

### Post by 133794m3r on 2008-06-12
yeah that didn't work at all... I can't even do that reconfigure thing and in the beginning it gives me a timer sync error. And also i can't even do anything in the terminal because the alt+F2 doesn't work... and the alt+F1 doesn't work...but the ctrl+alt+F1 does... and that won't let me do root.

---

### Post by kdcoetzee on 2008-06-12
sorry I was trying to say ctrl-alt-F1 but that slip my mind.

if you run the same command with a sudo in front.
that gives the command root privileges.

just for info: you can go into root with sudo -s -H.
sudo only gives the one command root privileges where "sudo -s -H" gives all the future command root privileges until you close the session.

sudo dpkg-reconfigure xserver-xorg

I should have added that from the begin aswell.

And as for the "timer sync error" I am not shore.
just check you BIOS time, and correct it if the time is incorrect.

---

### Post by 133794m3r on 2008-06-13
well I'm hoping that this will work then thanks for the help.
ok yeah I did that and all it did was ask me questions about my keyboard that was it. and that didn't do anything... my background still loads... but none of the panels show up... and also none of my desktop icons appear either.

---

