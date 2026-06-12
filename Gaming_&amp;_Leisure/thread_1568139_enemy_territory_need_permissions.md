---
title: "enemy territory need permissions"
date: 2010-09-04
forum: Gaming &amp; Leisure
---

### Post by rgbargee on 2010-09-04
really sorry for this but the permissions part of linux has me stumped

i have  followed the game guide for enemy territory and everything was going really well until i tried to run it. The installer goes through the licensing etc and then says it need permissions to install to the /usr directory

im really a beginner so if someone could point me in the right direction, ive searched through the forum quite a bit and found lots of entries for the keyword 'permissions' but not for this game installer anyone else had the same proble or is naivety showing

---

### Post by Carpentr on 2010-09-04
> **rgbargee said:**
> really sorry for this but the permissions part of linux has me stumped

i have  followed the game guide for enemy territory and everything was going really well until i tried to run it. The installer goes through the licensing etc and then says it need permissions to install to the /usr directory

im really a beginner so if someone could point me in the right direction, ive searched through the forum quite a bit and found lots of entries for the keyword 'permissions' but not for this game installer anyone else had the same proble or is naivety showing

When running the installer command through the terminal have you tried adding **sudo** in front of your command?

Example: **sudo** [command goes here without the brackets]

You should be prompted for your password, which will remove security permissions.

---

### Post by sakuramboo on 2010-09-05
Or, when it asks for the installation path, install it in your home directory.

---

### Post by rgbargee on 2010-09-06
For some reason i cant sudo the installer program so i changed the path to documents as this seems to be the only level at which i have permissions to write to. This seems to have worked round partially and is now installed :D. Now ive just got to sort out the sound which appears to be missing :-( Thanks for the help ill reply back if i manage to get some sound out of it .

---

