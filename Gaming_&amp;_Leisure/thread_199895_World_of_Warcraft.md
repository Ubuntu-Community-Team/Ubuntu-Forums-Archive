---
title: "World of Warcraft"
date: 2006-06-19
forum: Gaming &amp; Leisure
---

### Post by linux-newbie1 on 2006-06-19
Hello friends. I am a new user of linux and I am enjoying it very much and learning more each day (thanks to the wonderful community here)

Normally I play World of Warcraft on Windows XP but I decided to give it a go in Ubuntu. I got it working using Wine (with the wow patch version) and it works fine.
I am playing off the install on my WIndows partition (/media/hda1/Program Files/World of Warcraft/WoW.exe)

However when i change a setting like a graphical setting the next time i load up the settings are back to how they were before. I beleve it is becuase i cannot write to config file (/media/hda1/Program Files/World of Warcraft/WTF/Config.wtf)

I am wondering is it possible to allow writing to this file so i can keep the changes i make.

I hope this is clear for you to understand.
Many thanks.

---

### Post by justin whitaker on 2006-06-19
[QUOTE=linux-newbie1]Hello friends. I am a new user of linux and I am enjoying it very much and learning more each day (thanks to the wonderful community here)

Normally I play World of Warcraft on Windows XP but I decided to give it a go in Ubuntu. I got it working using Wine (with the wow patch version) and it works fine.
I am playing off the install on my WIndows partition (/media/hda1/Program Files/World of Warcraft/WoW.exe)

However when i change a setting like a graphical setting the next time i load up the settings are back to how they were before. I beleve it is becuase i cannot write to config file (/media/hda1/Program Files/World of Warcraft/WTF/Config.wtf)

I am wondering is it possible to allow writing to this file so i can keep the changes i make.

I hope this is clear for you to understand.
Many thanks.[/QUOTE]

You could copy the folder over to Linux, and edit the config file there.

---

### Post by eqisow on 2006-06-19
aye, you could copy the WoW folder to Linux and run it from there. The other option is enabling NTFS write support which is somewhat experimental and may mess up your XP partition.

If you cant's afford the HD space copying it to Linux would take and you don't want to risk your XP partition, then your only other option is to boot into Windows to change your WoW settings.

P.S. - You're going to run into a similiar problem when it comes to patching.

P.P.S. - If you decide you want to enable NTFS write suport, check [here]("http://www.ubuntuforums.org/showthread.php?t=142481").

---

