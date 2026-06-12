---
title: "Different themes for different desktops environments for the same user?"
date: 2018-11-15
forum: Desktop Environments
---

### Post by SourceSlayer on 2018-11-15
I have two desktop environments installed on one computer, one is Budgie, one is Unity. I like Ambience on Ubuntu and Picollo on Budgie, both seem to have to be set to all desktops simultaneously based on what's happening.

My current solution is something along the lines of creating a startup script for detecting the current desktop environment, changing the theme based on which it is (not sure how to do this yet), terminate script. 

While this seems like it may work well, it doesn't seem very elegant. Is there a proper way to do this?

---

### Post by Frogs Hair on 2018-11-16
Both DE's are currently gnome based and will display the same themes and icons. Budgie is slowly moving to QT and I have no idea how it will function as a second DE when this happens.

---

### Post by Tadaen_Sylvermane on 2018-11-16
I don't dual boot much anymore but it is the best way imo to do this. I use LVM for my disk partitioning. Disk space is cheap. I simply install a few copies of whatever, in this case Ubuntu. Each has it's own DE. Each installation has it's own dedicated /home. I have my normal /home/"$USER"/folders in a separate /data partition that is mounted in each one. 3 entire separate installations, no settings intermix and cause problems. And my data is available in all of them without any issue. Is probably a better way than this though.

---

