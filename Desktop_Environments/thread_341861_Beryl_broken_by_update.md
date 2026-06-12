---
title: "Beryl broken by update"
date: 2007-01-19
forum: Desktop Environments
---

### Post by CroEragon on 2007-01-19
Two weeks ago i god Beryl installed on my Ubuntu with ATI Radeon XPress 200 and it worked pretty fine except crashes once in while. Today some updates for Beryl available and I installed 'em without checking wha they are for. I turned off computer and now couple hours later my Beryl won't start. It starts Beryl Manager in systray but there is no wobbly logo on beginning and  Ubuntu reports crash few times. If i try to reload Windows manager it just tries loading Beryl and then fallback on Metacity without crash report.
Is there any way to undo updates or repair Beryl? Is this common problem with one of update or it is just me? Any help would be welcome.
Thanks in advance.
EDIT: Sorry for double topic, i just noticed it exist.

---

### Post by Mithrilhall on 2007-01-19
I'm also having  a problem with beryl ever since the update. I'm using an Intel i810 chipset.

---

### Post by Ear3ndil on 2007-01-19
I'm also using an i810 chipset with aiglx and have the same problem.

---

### Post by 360Mods on 2007-01-19
Everybody is having problems with the update.  I had to downgrade back to 1.4 to get it working again.  There is already an existing bug thread covering this topic, where Beryl people have acknowledge the bug and will update when fixed.

[http://ubuntuforums.org/showthread.php?t=341036]("http://ubuntuforums.org/showthread.php?t=341036")

---

### Post by jbus on 2007-01-19
Downgrade to the previous version with synaptic and don't update again until version 1.99.**[COLOR="Red"]1[/COLOR]** is released.

---

### Post by b1g4L on 2007-01-19
Yep, I had Beryl on XGL and it also crashed after the update. I'm using a Radeon 9800 pro. I believe last time I checked the Beryl team will be releasing a final version (non-beta) in late February. Hopefully complete with a new interface to tweak settings...

---

### Post by mysticmarks on 2007-01-19
I crashed after the update. I went in and discovered that the update preselects some features that many chipsets do not support. run both beryl and beryl manager as sudo once. if you get the manager up, go into your visual elements and try turning off most of the features, then do them one at a time and see what you can get up and running with. I had to disable window grouper, mipmap for desktop cube, and fading windows(which were not on by default earlier). after that i ran beryl sudo, got it back up, added _BOTH_ _beryl and beryl manager_ to my _session startup_ and now its great. beryl would crash without the sudo command until i had my manager settings correct again. Don't give up, the folks doing beryl are really doing a great job for so few people. They just don't have any way to be sure of what will work for which setup. I would suggest that you contact them add ask for all of the advanced features to be off by default in the next release. This should at least make getting up a cinch, and adjusting the settings from there on our own. It is a lot smoother now, and i haven't had any crashes. I have had to logout/in 2 or 3 times because desktop paper doesn't load right sometimes, but thats a ubuntu/gnome thing(did it before). They added jpeg support, nice. Sudo made the difference in getting it back up and configured again, dont give up! After you get it up and running again and the settings good again(they update realtime with changes, so just keep terminal open and load beryl after every manager change to see what happens), do a reboot and see if it loads ok. If not you may want to do a sudo chown * to the beryl directory, just to make sure all users get no issues loading. Check back soon.

---

### Post by Guillaumeb on 2007-01-19
how do you downgrade?

---

### Post by CroEragon on 2007-01-19
Just do what this qoute says:
> **vexeuz said:**
> Just revert back to old version:

for these packages: beryl; beryl-core; beryl-manager; beryl-plugins; beryl-plugins-data; beryl-settings; emerald; libberyldecoration0; libberylsettings0; libemeraldengine0

sudo apt-get update
(i hade to repeat code for each package):
sudo aptitude purge <packages>

Mine is back to normal. Just dont update these packages again if it ask you to...

---

